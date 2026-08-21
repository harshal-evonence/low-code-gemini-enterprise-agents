# Enterprise IT Runbook: DB Connection Pool Saturation & HTTP 504 Gateway Timeouts

**Document ID:** RB-OPS-042  
**Target Services:** User Authentication Service (`Auth-Prod-04`), Core API Gateway  
**Impacted Infrastructure:** DB Replica Node (`db-auth-prod-04`), Primary Auth DB Cluster  
**Owner:** Database Administration & Infrastructure Engineering Group  
**Classification:** Internal Restricted  
**Last Updated:** 2026-07-28  
**Version:** 4.0.0  

---

## 1. Incident Signature & Symptoms
Trigger this runbook if any of the following logging alerts are detected or user tickets report these exact symptoms:
- **System Metrics:** Connection pool utilization exceeds 95% (e.g., 142/150 connections active) for more than 3 consecutive minutes.
- **Latency Spikes:** Database response times spike beyond `5000ms` (normal operating threshold is `< 150ms`).
- **HTTP Response Codes:** Authentication endpoints return `HTTP 504 Gateway Timeout` or `HTTP 500 Internal Server Error (Database Connection Timeout)`.
- **User Experience:** Enterprise users globally cannot log in, encountering rotating loading spinners or timeout messages in Google Workspace tools.

---

## 2. Pre-Diagnostic Checklist
Before executing modifications, run these commands via your administrative terminal or check logs to verify environmental state:
1. Confirm network latency to the replica node:
   ```bash
   ping db-replica-04.enterprise.com
   ```
2. Verify if any scheduled database schema modification, migration, or ETL job is currently running by checking the **IT Operations Shared Google Calendar** for scheduled maintenance windows:
   - Search Calendar for: `"Database Migration"`, `"System Maintenance"`, or `"Auth Database Update"`.
3. Check the active thread count on `db-auth-prod-04`:
   ```sql
   SHOW PROCESSLIST;
   ```

---

## 3. Step-by-Step Remediation Protocol

### Step 3.1: Establish Secure Shell (SSH) Session
Establish an emergency administrative SSH session to the database replica node experiencing saturation:
```bash
ssh admin@db-replica-04.enterprise.com -p 2222
```

### Step 3.2: Flush Connection Pools
Force-flush the active database connection pools to immediately terminate hung or leaking connections:
```bash
/opt/scripts/flush_pool.sh --force --pool=auth-pool-04
```
*Expected Output:*
`[SUCCESS] Flushed 148 stalled connections from auth-pool-04. System resources returning to safe limits.`

### Step 3.3: Adjust Database Server Configurations
To prevent immediate re-saturation under peak load, scale the maximum allowed connections in the main service configuration file:
1. Open the configuration file:
   ```bash
   sudo vi /etc/db/auth-config.json
   ```
2. Locate the `"connection_settings"` block:
   ```json
   "connection_settings": {
     "max_connections": 150,
     "connection_timeout_ms": 15000,
     "idle_timeout_ms": 600000
   }
   ```
3. Update `"max_connections"` from `150` to `300`:
   ```json
   "connection_settings": {
     "max_connections": 300,
     "connection_timeout_ms": 15000,
     "idle_timeout_ms": 600000
   }
   ```
4. Save and exit the editor (`:wq!`).

### Step 3.4: Restart the Authentication Microservice
Gracefully restart the microservice on the app servers to apply the new connection pool configurations:
```bash
sudo systemctl restart auth-service.service
```

---

## 4. Post-Remediation & Verification
Execute the following commands to verify system recovery:
1. Ensure the auth service is running and healthy:
   ```bash
   sudo systemctl status auth-service.service
   ```
2. Perform a mock authentication call to verify latency:
   ```bash
   curl -w "@curl-format.txt" -o /dev/null -s -X POST https://auth.enterprise.com/v1/login -d '{"user":"test", "pass":"test"}'
   ```
   *Verify that "time_starttransfer" is less than 200ms.*
3. Verify that the current active database connection count is stabilized:
   ```sql
   SELECT count(*) FROM pg_stat_activity WHERE state = 'active';
   ```

---

## 5. Escalation & On-Call Contacts
If the connection pool immediately saturates again after flushing and scaling, escalate to the following on-call tiers:
*   **Tier 1:** Database Administration On-Call — +1-800-555-0191 (Page Code: DB-OPS)
*   **Tier 2:** Platform Reliability Engineer (SRE) Lead — sre-oncall@enterprise.com
*   **Tier 3:** Director of IT Operations — +1-800-555-0199
