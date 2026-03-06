# Security Auditor Tools & Integrations

## Vulnerability Scanning

### Trivy
- **Purpose**: Comprehensive vulnerability scanner for containers, images, repos
- **When to use**: Scanning Docker images, filesystems, Git repositories for vulnerabilities
- **Coverage**: CVEs in dependencies, misconfigurations, secrets
- **Risk level**: Low (read-only scanning)
- **Confirmation**: No

### Snyk
- **Purpose**: Developer-friendly vulnerability scanning and remediation
- **When to use**: Scanning for package vulnerabilities, license issues, IaC misconfigurations
- **Coverage**: NPM, PyPI, Maven, and many package managers; Terraform, Kubernetes configs
- **Risk level**: Low (read-only scanning, optional auto-fix)
- **Confirmation**: No for scanning; Yes for auto-fix recommendations

### OWASP Dependency-Check
- **Purpose**: Identify known vulnerable components
- **When to use**: Scanning for CVEs in Java, .NET, Python, JavaScript, Ruby dependencies
- **Coverage**: Multiple language ecosystems and databases
- **Risk level**: Low (read-only)
- **Confirmation**: No

### Safety (Python)
- **Purpose**: Python package vulnerability scanner
- **When to use**: Checking Python requirements for known vulnerabilities
- **Common operations**: `safety check`, vulnerability database search
- **Risk level**: Low (read-only)
- **Confirmation**: No

## Secret Scanning

### git-secrets
- **Purpose**: Prevent and detect secrets in Git repositories
- **When to use**: Scanning commits for API keys, credentials, tokens
- **Common operations**: `scan`, `add patterns`, `clean history`
- **Risk level**: Low (read-only detection)
- **Confirmation**: Yes for destructive history rewriting

### TruffleHog
- **Purpose**: Search for secrets in Git history and sources
- **When to use**: Deep scanning of repositories for accidentally committed secrets
- **Coverage**: API keys, passwords, AWS keys, Slack tokens, private keys
- **Risk level**: Low (read-only)
- **Confirmation**: No

### detect-secrets
- **Purpose**: Identify and prevent secrets in code
- **When to use**: Baseline generation, detecting secrets in files
- **Features**: Entropy-based detection, plugin patterns
- **Risk level**: Low (read-only)
- **Confirmation**: No

### Vault / HashiCorp Vault Audit
- **Purpose**: Secrets management security validation
- **When to use**: Auditing secret storage implementation, access patterns
- **Coverage**: Secret access logs, policy compliance, key rotation
- **Risk level**: Low (audit log review)
- **Confirmation**: No

## SAST (Static Application Security Testing)

### Semgrep
- **Purpose**: Open source static analysis with custom rule support
- **When to use**: Scanning for code vulnerabilities, security patterns, misconfigurations
- **Coverage**: Python, JavaScript, Java, Go, C, C++, more
- **Risk level**: Low (read-only analysis)
- **Confirmation**: No

### SonarQube
- **Purpose**: Comprehensive code quality and security analysis
- **When to use**: Identifying bugs, vulnerabilities, code smells
- **Coverage**: 27+ languages, security hotspot detection
- **Risk level**: Low (read-only)
- **Confirmation**: No

### Checkmarx / Fortify
- **Purpose**: Enterprise static analysis for security
- **When to use**: Comprehensive vulnerability scanning in large enterprises
- **Coverage**: Thousands of vulnerability patterns
- **Risk level**: Low (read-only)
- **Confirmation**: No

## Configuration & Infrastructure Scanning

### nmap
- **Purpose**: Network port scanning and service enumeration
- **When to use**: Identifying open ports, exposed services, network exposure
- **Common operations**: `nmap -sV`, vulnerability detection
- **Risk level**: Medium (active network scanning)
- **Confirmation**: Yes for production scans; No for lab environments

### Tenable Nessus / OpenVAS
- **Purpose**: Vulnerability scanner for networks and infrastructure
- **When to use**: Comprehensive vulnerability assessment of systems
- **Coverage**: CVEs, misconfigurations, weak protocols
- **Risk level**: Medium (active scanning, can cause disruption)
- **Confirmation**: Yes for production scans

### Prowler
- **Purpose**: AWS security assessment
- **When to use**: Auditing AWS account configuration and compliance
- **Coverage**: 240+ checks against CIS AWS Foundations Benchmark
- **Risk level**: Low (read-only API calls)
- **Confirmation**: No

### ScoutSuite / CloudMapper
- **Purpose**: Cloud security posture assessment
- **When to use**: Multi-cloud infrastructure audit (AWS, Azure, GCP)
- **Coverage**: IAM, networking, encryption, compliance
- **Risk level**: Low (read-only API calls)
- **Confirmation**: No

### Terraform / IaC Scanning (tfsec, Checkov)
- **Purpose**: Infrastructure-as-Code security assessment
- **When to use**: Finding misconfigurations in Terraform, CloudFormation, Kubernetes
- **Coverage**: Security best practices, compliance standards
- **Risk level**: Low (static file analysis)
- **Confirmation**: No

### Kube-bench / Kube-score
- **Purpose**: Kubernetes security and compliance checks
- **When to use**: Auditing Kubernetes cluster configuration
- **Coverage**: CIS Kubernetes Benchmark, pod security policies
- **Risk level**: Low (read-only queries)
- **Confirmation**: No

## Network Security

### SSL/TLS Assessment
- **testssl.sh** — SSL/TLS configuration auditor
  - When: Validating certificate quality, protocol versions, cipher strength
  - Risk: Low (read-only scanning)

- **nmap --script ssl-enum-ciphers** — Cipher enumeration
  - When: Identifying weak cipher suites
  - Risk: Low (read-only)

### DNS Security
- **dig / nslookup** — DNS query tools
  - When: Checking DNSSEC, DNS records, resolving hostnames
  - Risk: Low (read-only)

- **host / whois** — Domain/host information
  - When: Enumerating domains, checking registrants
  - Risk: Low (read-only)

## Authentication & Access Control

### IAM Auditors
- **CloudMapper** (AWS) — IAM privilege mapping
  - When: Analyzing IAM policies and privilege levels
  - Risk: Low (read-only)

- **Azure Security Center** — Azure IAM auditing
  - When: Reviewing Azure access controls
  - Risk: Low (read-only)

### Password Security
- **John the Ripper** — Password cracking (lab only)
  - When: Testing password strength in lab/authorized environment
  - Risk: High (destructive testing)
  - Confirmation: Yes, only in authorized/lab environment

## Data Protection & Encryption

### Encryption Validators
- **openssl** — SSL/TLS and certificate analysis
  - When: Validating encryption configuration, certificate validation
  - Risk: Low (read-only)

- **HashiCorp Vault CLI** — Secrets management audit
  - When: Auditing secret access, key rotation
  - Risk: Low (read-only audit logs)

### Key Management Audit
- **AWS KMS** audit tools
  - When: Assessing key management and rotation
  - Risk: Low (read-only)

## Logging & Monitoring Assessment

### Log Analysis
- **Splunk / ELK (read access)** — Log analysis and searching
  - When: Reviewing security events and incidents
  - Risk: Low (read-only)

- **CloudTrail (AWS) / Audit Logs** — Activity logging review
  - When: Checking audit logging completeness
  - Risk: Low (read-only)

### SIEM Integration
- **Alert review and trending**
  - When: Assessing monitoring effectiveness
  - Risk: Low (read-only)

## Compliance & Audit

### Compliance Frameworks
- **CIS Benchmarks** — Baseline security standards
  - When: Assessing compliance with CIS standards
  - Risk: Low (audit reference)

- **NIST Cybersecurity Framework** — Security assessment framework
  - When: Evaluating against NIST standards
  - Risk: Low (audit framework)

- **PCI-DSS, HIPAA, GDPR tools** — Compliance validators
  - When: Assessing compliance with regulations
  - Risk: Low (audit assessment)

### Audit Tools
- **Compliance automation platforms** (Scout, Cloudinary, etc.)
  - When: Tracking compliance requirements and status
  - Risk: Low (audit tracking)

## Application Testing

### Dynamic Application Security Testing (DAST)
- **OWASP ZAP** — Web application security scanner
  - When: Dynamic testing of web applications for vulnerabilities
  - Risk: Medium (active testing)
  - Confirmation**: Yes for production testing

- **Burp Suite** — Web security testing platform
  - When: Comprehensive web application penetration testing
  - Risk: Medium-High (active testing)
  - Confirmation: Yes, requires explicit authorization

## Threat Intelligence

### Vulnerability Databases
- **National Vulnerability Database (NVD)** — CVE database
  - When: Researching vulnerabilities and CVE details
  - Risk: Low (read-only reference)

- **GitHub Security Advisory Database** — GitHub vulnerability data
  - When: Checking for vulnerabilities in dependencies
  - Risk: Low (read-only)

### Threat Feeds
- **OSINT sources** — Open source intelligence
  - When: Tracking new threats, exploits, malware
  - Risk: Low (read-only)

## Reporting & Documentation

### Report Generation
- **Automated report builders** in major scanner tools
  - Purpose: Generate assessments and findings reports
  - Risk: Low (documentation)

- **Executive summary generators**
  - Purpose: Create business-focused security reports
  - Risk: Low (documentation)

## Incident Response Tools

### Log Preservation
- **Evidence collection tools**
  - When: Gathering logs and data for breach investigation
  - Risk: Medium (evidence handling)
  - Confirmation: Yes for chain of custody

### Timeline Analysis
- **Event log analysis tools**
  - When: Reconstructing incident timeline
  - Risk: Low (read-only analysis)

---

## Tool Usage Guidelines

### Authorization Requirements
- Vulnerability scanning: Documented scope and authorization
- Network scanning: Explicit written authorization from IT/security
- Penetration testing: Signed engagement agreement required
- Secret scanning: Code repository access needed
- Configuration audit: Read-only access to systems

### Safe Testing Practices
1. Run against non-production first when possible
2. Schedule production scans during maintenance windows
3. Coordinate with infrastructure teams
4. Monitor for scan impact (CPU, bandwidth)
5. Preserve all scan results for trending
6. Document baseline and changes

### False Positive Management
- Automated tools generate false positives—manually verify
- Prioritize high-confidence findings
- Document and suppress known false positives
- Adjust tool configurations to reduce noise
- Balance sensitivity vs. false positive rate

### Scanning Best Practices
- Run scans regularly (weekly minimum)
- Use multiple tools to cross-validate findings
- Compare results over time (trending)
- Investigate all new findings
- Document remediation actions
- Re-scan after fixes to confirm

### Severity & Priority
- Focus on CRITICAL and HIGH findings first
- Set realistic remediation timelines
- Balance urgency with business operations
- Communicate timeline to stakeholders
- Track and report on progress

### Tool Versions & Updates
- Keep scanning tools updated
- Update vulnerability databases daily
- Test updates in staging first
- Document tool versions in reports
- Archive old reports for trending
