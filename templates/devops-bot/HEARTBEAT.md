# DevOps Bot - Health Check & Monitoring

## Heartbeat Configuration

### Service Health Checks

#### Kubernetes Cluster Health
```
Check every: 30 seconds
Timeout: 10 seconds
Endpoint: kubectl cluster-info dump | jq '.cluster-status'

Healthy when:
- All control plane nodes running
- API server responding
- etcd cluster quorum established
- Scheduler and controller-manager running

Alert on:
- API server unavailable (CRITICAL)
- Quorum loss (CRITICAL)
- Any control plane node down (HIGH)
- etcd high latency >100ms (MEDIUM)
```

#### Docker Registry Health
```
Check every: 1 minute
Timeout: 5 seconds
Endpoint: docker registry health check endpoint

Healthy when:
- Registry responding to health probes
- Storage backend accessible
- No auth failures

Alert on:
- Registry unavailable (HIGH)
- Storage failures (HIGH)
- High push latency >5s (MEDIUM)
```

#### Cloud Provider API Connectivity
```
Check every: 60 seconds
Timeout: 10 seconds
Endpoints:
- aws-cli sts get-caller-identity
- gcloud auth list
- az account show

Healthy when:
- All providers responding
- Credentials valid
- Rate limits not exceeded

Alert on:
- Any provider unreachable (HIGH)
- Credential expiration <7 days (MEDIUM)
- Rate limit approaching (MEDIUM)
```

### Agent Operational Status

#### Tool Availability
```
Check every: 5 minutes
Verify installation of:
- kubectl (minimum version 1.20)
- Helm (minimum version 3.0)
- Terraform (minimum version 0.14)
- Docker (minimum version 20.10)
- aws-cli (minimum version 2.0)
- gcloud (current version)
- Ansible (minimum version 2.10)

Alert on:
- Missing critical tool (HIGH)
- Version mismatch with production requirements (MEDIUM)
- Tool command failures (MEDIUM)
```

#### Credential & Token Freshness
```
Check every: 30 minutes
Verify validity of:
- Kubernetes API tokens
- Cloud provider credentials
- Container registry authentication
- Vault tokens (if applicable)

Alert on:
- Token expiration <1 hour (HIGH)
- Credential rotation overdue (MEDIUM)
- Failed authentication attempts (HIGH)
```

#### System Resources
```
Check every: 10 seconds
Monitor:
- Agent process memory usage (target <500MB)
- CPU utilization (target <20%)
- Disk space for artifacts and logs (target >10GB free)
- Network connectivity to critical endpoints

Alert on:
- Memory exceeding 1GB (HIGH)
- CPU sustained >80% (MEDIUM)
- Disk space <2GB (CRITICAL)
- Network connectivity loss >30s (HIGH)
```

## Monitoring Endpoints

### Metrics Export
```
Endpoint: /metrics
Format: Prometheus format
Metrics:
- agent_operations_total
- agent_operation_duration_seconds
- agent_deployments_successful
- agent_deployments_failed
- agent_incident_resolutions
- agent_cluster_health_status
- agent_authentication_failures

Refresh: Every 15 seconds
```

### Status Dashboard
```
Endpoint: /status/dashboard
Displays:
- Current cluster health status
- Recent deployments and outcomes
- Pending confirmations
- Active alerts
- Tool availability
- Performance metrics

Refresh: Real-time updates
```

### Availability Status
```
Endpoint: /health
Response format: JSON
Healthy response:
{
  "status": "healthy",
  "timestamp": "2026-03-05T14:30:45Z",
  "uptime_seconds": 86400,
  "tools_available": ["kubectl", "helm", "terraform", "docker", "aws-cli", "gcloud"],
  "cluster_connections": 3,
  "last_successful_operation": "2026-03-05T14:28:12Z"
}

HTTP Status Codes:
- 200: Fully operational
- 202: Degraded but functional (some tools unavailable)
- 503: Non-operational (critical dependencies missing)
```

## Incident Response Readiness

### On-Call Checklist
Daily (automated):
- [ ] Verify cluster connectivity
- [ ] Validate credential freshness
- [ ] Check tool versions match production
- [ ] Review recent deployment success rate
- [ ] Test alert channels (Slack, PagerDuty, etc.)
- [ ] Verify access to incident runbooks

### Alert Routing
```
CRITICAL alerts:
- PagerDuty (immediate page)
- Slack #incidents channel (mention @on-call)
- Email backup (if other channels fail)

HIGH alerts:
- Slack #incidents channel
- Email notification

MEDIUM alerts:
- Slack #incidents channel (no page)
- Added to daily report

LOW alerts:
- Daily digest only
```

### Escalation Procedures
```
0-5 minutes: Automated triage and initial remediation attempt
5-15 minutes: Alert on-call team if issue persists
15+ minutes: Escalate to team lead and incident commander
30+ minutes: Engage subject matter experts and senior staff
```

## Performance Baselines

### Expected Operation Times
```
Cluster health check: <2 seconds
Deployment to 8 replicas: 60-120 seconds
Terraform plan on 100+ resources: 30-60 seconds
Kubernetes backup creation: 5-15 minutes
Log query (1 hour window): <5 seconds
Metric query (24 hour window): <10 seconds
```

### Success Rate Targets
```
Deployment success rate: >99%
Incident detection time: <60 seconds
Mean time to resolution: <15 minutes
Authentication success rate: >99.9%
Tool availability: >99.5%
```

## Maintenance Windows

### Scheduled Maintenance
```
Frequency: Monthly
Duration: 30 minutes
Preferred timing: Tuesday 02:00-02:30 UTC (off-peak)

Activities:
- Tool version updates
- Credential rotation
- Configuration backup
- Performance baseline resets
```

### Dependency Monitoring
```
Check for updates:
- Kubernetes updates (monthly)
- Cloud provider CLI updates (monthly)
- Terraform updates (quarterly)
- Ansible updates (quarterly)

Notify when:
- Security patch available (CRITICAL)
- Major version available (INFO)
```

## Logging & Audit

### Operational Logs
```
Destination: Structured logging to Elasticsearch/ELK
Log level: INFO (default), DEBUG (on request)
Retention: 90 days
Search: Queryable via Kibana dashboard
Fields captured:
  - timestamp
  - operation_type
  - user/requestor
  - cluster_context
  - success/failure
  - duration
  - affected_resources
  - authorization_status
```

### Audit Trail
```
Captured for all:
- Destructive operations (delete, destroy, update)
- Production changes
- Credential access
- Authorization changes
- Incident response actions

Immutable storage: Yes
Retention: 1 year
Access: Limited to audit team + SIEM system
```

## Recovery Procedures

### If Agent Becomes Unhealthy
1. Check system resources (memory, disk, CPU)
2. Verify network connectivity to critical services
3. Test API authentication and token refresh
4. Review recent logs for error patterns
5. Restart agent if needed (graceful shutdown + restart)
6. Run diagnostic tools to validate cluster connectivity
7. Alert team if recovery fails

### If Cluster Connectivity Lost
1. Verify network connectivity to cluster endpoints
2. Check API server status
3. Validate credentials and tokens
4. Try alternate cluster endpoints if available
5. Fall back to last-known-good state
6. Escalate to infrastructure team

### If Tools Become Unavailable
1. Verify tool installation and versions
2. Check if tool authentication is required
3. Update or reinstall tool if needed
4. Test tool functionality independently
5. Notify team of degraded capability
6. Continue with available tools where possible

## Contact & Escalation

**Primary Contact:** On-call DevOps Engineer
**Escalation:** DevOps Team Lead
**Emergency:** Page on-call via PagerDuty

**Status Page:** https://status.infra.internal
**Runbook Location:** https://wiki.internal/infra/runbooks
**Incident Channel:** #incidents (Slack)
