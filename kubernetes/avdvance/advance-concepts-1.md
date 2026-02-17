### 🚪 Ingress

Ingress is a smart router.
It manages external HTTP(S) access to your services.
**You define rules like:**
/api → backend-service
/ → frontend-service

Works with an **Ingress Controller** (e.g., **NGINX**, **Traefik**).
Replaces the need for multiple **LoadBalancers**.

### 🕒 CronJob

A **CronJob** runs tasks on a schedule (like **Linux cron**).

**Useful for:**

- Backups.
- Reports.
- Periodic data processing.
- schedule: "0 0 \* \* \*" # daily at midnight
