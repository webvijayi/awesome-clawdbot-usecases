# 🖥️ Server Health Monitor

> Sleep peacefully. Your servers are watched 24/7.

---

## The Problem

Server issues don't wait for business hours. A crashed service at 3 AM means lost revenue, angry users, and frantic troubleshooting while half-asleep. Most monitoring tools just send alerts—they don't help you fix anything.

---

## The Solution

Clawdbot continuously monitors your infrastructure, alerts you intelligently (not for every blip), attempts automatic remediation for known issues, and provides context when you need to investigate.

---

## Setup Guide

### Step 1: Install Monitoring Skills (5 minutes)

```bash
clawdbot skill install uptime-kuma
clawdbot skill install proxmox  # if using Proxmox
clawdbot skill install hetzner-cloud  # if using Hetzner
clawdbot skill install digital-ocean  # if using DO
clawdbot skill install pm2  # for Node.js apps
```

### Step 2: Configure Uptime Kuma

Create `~/clawd/monitoring/config.json`:

```json
{
  "uptimeKuma": {
    "url": "https://status.yourdomain.com",
    "apiKey": "your-api-key"
  },
  "alertThresholds": {
    "cpuPercent": 90,
    "memoryPercent": 85,
    "diskPercent": 90,
    "responseTimeMs": 2000
  },
  "quietHours": {
    "enabled": true,
    "start": "23:00",
    "end": "07:00",
    "exceptCritical": true
  }
}
```

### Step 3: Define Auto-Remediation Rules

Create `~/clawd/monitoring/remediation.md`:

```markdown
# Auto-Remediation Playbook

## High Memory Usage
1. Check top memory consumers: `ps aux --sort=-%mem | head -10`
2. Clear system cache if safe: `sync && echo 3 > /proc/sys/vm/drop_caches`
3. Restart specific service if identified

## Service Down
1. Check service status: `systemctl status {service}`
2. Check logs: `journalctl -u {service} -n 50`
3. Attempt restart: `systemctl restart {service}`
4. If fails, escalate immediately

## Disk Full
1. Find large files: `du -h / | sort -rh | head -20`
2. Clear old logs: `journalctl --vacuum-time=7d`
3. Clear package cache: `apt clean` / `yum clean all`
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `uptime-kuma` | Monitor uptime and response times |
| `proxmox` | VM/container management |
| `hetzner-cloud` | Hetzner server management |
| `digital-ocean` | DO droplet management |
| `pm2` | Node.js process management |
| `gotify` | Push notifications |

---

## Example Prompts

**Check all systems:**
```
Give me a health report on all monitored servers. Any issues in the last 24 hours?
```

**Investigate an alert:**
```
Server [name] CPU is at 95%. What's consuming resources? Can you safely reduce load?
```

**Scheduled maintenance:**
```
I need to restart the database server tonight at 2 AM. Set up a maintenance window and notify me when it's back up.
```

**Capacity planning:**
```
Show me resource trends for the past month. Which servers are approaching capacity limits?
```

---

## Cron Schedule

```
*/5 * * * *    # Every 5 min - quick health check
0 * * * *      # Hourly - detailed metrics collection
0 8 * * 1      # Monday 8 AM - weekly health report
0 0 1 * *      # 1st of month - capacity planning report
```

---

## HEARTBEAT.md Config

```markdown
## Server Monitoring
- [ ] All critical services UP?
- [ ] Any resource above threshold?
- [ ] SSL certs expiring within 14 days?
- [ ] Backup jobs completed successfully?
```

---

## Expected Results

**Week 1:**
- All servers monitored in one place
- Alert fatigue reduced by 70%

**Month 1:**
- 50% of routine issues auto-remediated
- MTTR (Mean Time To Recovery) down 60%
- Clear visibility into infrastructure health

**Month 3:**
- Proactive capacity planning prevents outages
- Historical data drives optimization decisions
- Sleep through the night confidently
