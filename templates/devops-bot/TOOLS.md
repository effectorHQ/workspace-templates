# DevOps Tools & Integrations

## Container Orchestration

### kubectl
- **Purpose**: Kubernetes cluster management and debugging
- **When to use**: Pod operations, deployment updates, cluster diagnostics, resource inspection
- **Common operations**: `get pods`, `describe node`, `logs`, `exec`, `apply`, `delete`
- **Risk level**: High (can modify cluster state)
- **Confirmation**: Yes for destructive operations (delete, scale down critical services)

### Helm
- **Purpose**: Kubernetes package management and chart deployment
- **When to use**: Installing/upgrading services, managing releases, template rendering
- **Common operations**: `helm install`, `helm upgrade`, `helm rollback`, `helm list`
- **Risk level**: Medium-High (upgrades can cause disruptions)
- **Confirmation**: Yes before applying changes to production

### docker
- **Purpose**: Container image building, testing, and debugging
- **When to use**: Building images, testing locally before pushing to registry, debugging container issues
- **Common operations**: `build`, `run`, `push`, `logs`, `exec`, `inspect`
- **Risk level**: Low (local operations) to High (pushing to registry used in production)
- **Confirmation**: No for local testing; Yes for pushing production images

## Infrastructure-as-Code

### Terraform
- **Purpose**: Multi-cloud infrastructure provisioning and management
- **When to use**: Creating/modifying cloud resources, managing infrastructure state, planning changes
- **Common operations**: `terraform plan`, `terraform apply`, `terraform destroy`, `terraform state`
- **Risk level**: Very High (can provision/destroy significant infrastructure)
- **Confirmation**: Yes for all production applies; show plan first
- **Special handling**: Always review state files; confirm cost estimates before apply

### Ansible
- **Purpose**: Node configuration management and large-scale automation
- **When to use**: Applying configurations to multiple hosts, patching systems, managing services
- **Common operations**: `ansible-playbook`, `ansible-inventory`, `ansible-lint`
- **Risk level**: High (changes affect multiple systems simultaneously)
- **Confirmation**: Yes for production playbooks; dry-run recommended

## Cloud Provider CLIs

### aws-cli
- **Purpose**: Amazon Web Services resource management
- **When to use**: EC2, RDS, S3, Lambda, CloudFront, VPC, IAM operations
- **Common operations**: `ec2 describe-instances`, `rds describe-db-instances`, `s3 ls`, `iam list-users`
- **Risk level**: Medium-High (depends on operation scope)
- **Confirmation**: Yes for destructive operations (terminate, delete); Yes for IAM changes
- **Special handling**: Check credentials before operations; verify region context

### gcloud
- **Purpose**: Google Cloud Platform resource management
- **When to use**: GKE, Compute Engine, Cloud SQL, Cloud Storage, Cloud Run operations
- **Common operations**: `gcloud compute instances list`, `gcloud container clusters describe`, `gcloud sql instances`
- **Risk level**: Medium-High (depends on operation)
- **Confirmation**: Yes for destructive operations; Yes for creating resources
- **Special handling**: Verify active project/region; authentication scoping

### az (Azure CLI)
- **Purpose**: Microsoft Azure resource management
- **When to use**: VMs, AKS, Azure SQL, Storage accounts, RBAC management
- **Common operations**: `az vm list`, `az aks get-credentials`, `az storage blob list`
- **Risk level**: Medium-High (scope-dependent)
- **Confirmation**: Yes for resource creation/deletion; Yes for configuration changes
- **Special handling**: Subscription context verification

## Monitoring & Observability

### Prometheus
- **Purpose**: Metrics collection and time-series data retrieval
- **When to use**: Querying metrics, validating alerting rules, capacity planning
- **Common operations**: PromQL queries, scrape config verification, target health checks
- **Risk level**: Low (read-only typically)
- **Confirmation**: No (read operations)
- **Special handling**: Performance impact for expensive queries; rate-limit testing

### Grafana
- **Purpose**: Metrics visualization and dashboard management
- **When to use**: Creating/updating dashboards, alert testing, metric exploration
- **Common operations**: Dashboard creation, panel updates, alert configuration
- **Risk level**: Low-Medium (visualization only, but alerting changes are high risk)
- **Confirmation**: Yes for alert rule changes; No for visualization updates

### Datadog / New Relic
- **Purpose**: Full-stack monitoring and APM
- **When to use**: Application performance monitoring, infrastructure monitoring, log aggregation
- **Common operations**: Dashboard creation, alert configuration, metric exploration
- **Risk level**: Medium (alerting changes affect incident response)
- **Confirmation**: Yes for alert rule changes; No for dashboard/query updates

### Elasticsearch / Kibana
- **Purpose**: Log storage, indexing, and analysis
- **When to use**: Log searching, debugging, trace analysis, performance investigation
- **Common operations**: Index queries, snapshot creation, retention policy updates
- **Risk level**: Low-Medium (read-heavy); High for index deletion
- **Confirmation**: Yes for destructive operations; No for searches/analysis

## Deployment & CI/CD

### git
- **Purpose**: Version control operations
- **When to use**: Code checkout, branch operations, commit history review
- **Common operations**: `clone`, `checkout`, `log`, `diff`, `merge`
- **Risk level**: Low (read operations) to Medium (merging/pushing)
- **Confirmation**: No for read operations; Yes for pushing to main branches

### GitHub Actions / GitLab CI / Jenkins
- **Purpose**: CI/CD pipeline definition and execution
- **When to use**: Triggering deployments, querying build history, debugging pipeline failures
- **Common operations**: Trigger builds, retrieve artifacts, check log outputs
- **Risk level**: Medium-High (pipelines deploy code to production)
- **Confirmation**: Yes for triggering production deployments
- **Special handling**: Environment validation before triggering

## Security & Secrets

### git-secrets
- **Purpose**: Prevent secret/credential leakage in repositories
- **When to use**: Pre-commit scanning, secret remediation, credential rotation checks
- **Common operations**: Scanning commits for patterns, removing secrets from history
- **Risk level**: Low (preventive)
- **Confirmation**: No for scans; Yes for destructive rewriting of history

### AWS Secrets Manager / Azure Key Vault / Google Secret Manager
- **Purpose**: Secrets and credential storage
- **When to use**: Rotating secrets, managing credentials, auditing access
- **Common operations**: `get-secret`, `create-secret`, `rotate-secret`, `list-secrets`
- **Risk level**: Very High (sensitive credential access)
- **Confirmation**: Yes for all operations; Log all access
- **Special handling**: Never display secrets in logs; use only in necessary contexts

### HashiCorp Vault
- **Purpose**: Centralized secrets and encryption management
- **When to use**: Issuing dynamic credentials, rotating secrets, audit logging
- **Common operations**: `vault kv get`, `vault kv put`, token generation
- **Risk level**: Very High (credential authority)
- **Confirmation**: Yes for all operations; Audit logs mandatory

## Network & Troubleshooting

### kubectl port-forward / kubectl exec
- **Purpose**: Debug containers and test services
- **When to use**: Connecting to services for testing, running diagnostic commands, log inspection
- **Common operations**: Port forwarding, shell access, running diagnostic tools
- **Risk level**: Medium (debugging access to systems)
- **Confirmation**: No for read-only operations; caution for exec commands

### tcpdump / netstat / ss
- **Purpose**: Network diagnostics and packet inspection
- **When to use**: Investigating connectivity issues, analyzing traffic patterns, debugging network problems
- **Common operations**: Packet capture, connection state inspection, traffic analysis
- **Risk level**: Low (observational)
- **Confirmation**: No
- **Special handling**: Be aware of PII in packet capture data

### dig / nslookup / curl
- **Purpose**: DNS resolution and HTTP testing
- **When to use**: Validating DNS records, testing API endpoints, debugging connectivity
- **Common operations**: DNS queries, endpoint testing, header inspection
- **Risk level**: Low (read-only)
- **Confirmation**: No

## Backup & Disaster Recovery

### velero / etcd backup
- **Purpose**: Kubernetes cluster backups and disaster recovery
- **When to use**: Creating backups, restoring from backups, validating backup integrity
- **Common operations**: `velero backup create`, `velero restore`, schedule validation
- **Risk level**: High (restore can overwrite cluster state)
- **Confirmation**: Yes for restore operations; recommend backup verification first

### Database Backups (mysqldump, pg_dump, mongodump)
- **Purpose**: Database point-in-time recovery
- **When to use**: Creating snapshots before major changes, backup verification, retention management
- **Common operations**: Snapshot creation, backup listing, restore testing
- **Risk level**: High (restore affects data)
- **Confirmation**: Yes for restore operations

## Cost Management

### cloud cost analysis tools (AWS Cost Explorer, GCP Billing, Azure Cost Management)
- **Purpose**: Cost tracking and optimization
- **When to use**: Budgeting, identifying cost anomalies, optimizing resource allocation
- **Common operations**: Historical analysis, forecasting, resource right-sizing recommendations
- **Risk level**: Low (informational)
- **Confirmation**: No (read-only)

---

## Tool Safety Guidelines

### Before Using Any Tool
1. Verify the correct environment/cluster/region context
2. For production operations: Show the plan before execution
3. For destructive operations: Confirm blast radius and rollback procedure
4. For sensitive data: Ensure appropriate access controls and audit logging

### Error Handling
- If a tool command fails, check: credentials, permissions, resource existence, quota limits
- For partial failures, isolate and retry rather than wholesale rollback
- Always preserve error output for incident investigation

### Performance Considerations
- Some operations (large cluster operations, expensive queries) can impact system performance
- Use dry-run modes when available
- Throttle operations to avoid cascading failures
