## Security Architecture Review

**Task:** Review security architecture design for weaknesses and provide hardening recommendations

**Advanced Techniques:** Threat modeling, defense-in-depth assessment, attack path analysis, security control evaluation

**Principles Applied:** Context (business requirements + threat landscape), Structure (layered assessment), Specificity (concrete recommendations), Iteration (refinement based on constraints)

```markdown
You are a security architect conducting a security review of [SYSTEM/INFRASTRUCTURE/APPLICATION] architecture. Your goal is to identify security weaknesses, assess risk, and provide prioritized remediation recommendations that balance security with operational requirements.

ARCHITECTURE REVIEW SCOPE:
- System/Application: [NAME_AND_PURPOSE]
  🏢 Enterprise: "System: Customer Portal Application (external-facing web app for patient record access). Tech stack: React frontend, Node.js API, PostgreSQL database, deployed on AWS."
  🌐 Consumer: "External-facing web application with database backend, cloud-hosted."

- Review Driver: [WHY_NOW]
  Example: "Driver: Pre-production security review before public launch. Required per SDLC policy for internet-facing applications handling sensitive data."

- Business Context: [CRITICALITY]
  Example: "Business criticality: HIGH - Core customer-facing service, processes [data type], downtime impacts [X] users and revenue."

- Threat Model: [PRIMARY_CONCERNS]
  Example: "Primary threats: External attackers (credential stuffing, SQLi, XSS), Data breach (PII/PHI exposure), Service disruption (DDoS, availability)."

ARCHITECTURE DOCUMENTATION:
Provide or reference available architecture documentation:

🏢 Enterprise: Include actual architecture details
"Architecture Docs Available:
- System architecture diagram (Lucidchart): [Link]
- Network topology (Visio): [Link]
- Data flow diagrams: [Link]
- Component inventory: [spreadsheet]
- API documentation: [Swagger/OpenAPI spec]
- Infrastructure as Code: [Terraform/CloudFormation repo]
- Security controls matrix: [Document listing implemented controls]

Technology Stack:
- Frontend: React 18, hosted on CloudFront CDN
- API Layer: Node.js 18 (Express), containerized (Docker), running on ECS Fargate
- Database: PostgreSQL 14, RDS Multi-AZ
- Authentication: Auth0 (third-party IdP), OAuth 2.0/OIDC
- Cloud: AWS (us-east-1 region)
- Secrets Management: AWS Secrets Manager
- Monitoring: CloudWatch, Application logs to ELK stack"

🌐 Consumer: Keep details generic
"Architecture documentation provided separately.

Technology Stack (high-level):
- Frontend: Modern JavaScript framework, CDN-delivered
- API: Container-based microservices
- Database: Relational database, managed service
- Authentication: Third-party identity provider, modern protocols
- Cloud: Public cloud infrastructure
- Monitoring: Centralized logging and alerting"

REVIEW APPROACH:
- Review Type: [COMPREHENSIVE / FOCUSED / RAPID]
  Example: "COMPREHENSIVE review: Full architecture assessment across all layers (network, application, data, identity)."

- Assessment Method: [DOCUMENT_REVIEW / INTERVIEWS / TESTING / HYBRID]
  Example: "HYBRID: Documentation review + technical interviews with dev/ops teams + limited technical validation (architecture testing, not penetration testing)."

- Time Allocated: [DURATION]
  Example: "2 weeks: 1 week for assessment, 1 week for report and recommendations."

ORGANIZATIONAL CONSTRAINTS:
- Security Maturity: [LEVEL]
  Example: "Moderate security maturity: Have basic security controls (firewalls, AV, patching), but limited security engineering resources, no dedicated AppSec team."

- Resource Constraints: [BUDGET_PEOPLE_TIME]
  🏢 Enterprise: "Budget: $50K for immediate remediation, $200K for long-term improvements in next fiscal year. Team: 2 cloud engineers, 1 security engineer (part-time allocation)."
  🌐 Consumer: "Limited budget for immediate fixes, constrained engineering resources."

- Operational Constraints: [UPTIME_REQUIREMENTS]
  Example: "Uptime SLA: 99.9% (43 minutes/month downtime allowed). Changes require testing in staging, deployment windows: Sunday 2-6am EST."

- Compliance Requirements: [REGULATIONS]
  🏢 Enterprise: "HIPAA compliance required (PHI data), SOC 2 Type II in progress, state privacy laws (CCPA, CDPA)."
  🌐 Consumer: "Healthcare regulations, privacy law compliance requirements."

---

ARCHITECTURE SECURITY REVIEW METHODOLOGY:

Structure review across multiple security dimensions:

**PHASE 1: THREAT MODELING**

Identify threats specific to this architecture:

**Assets Requiring Protection**:
```
Critical Assets:
1. Patient Health Information (PHI):
   - Data: Names, DOB, SSN, medical records, insurance info
   - Storage: PostgreSQL database (RDS)
   - Sensitivity: HIGHEST (HIPAA-protected, breach notification required)
   - Threat: Unauthorized access, data breach, insider threat

2. Authentication Credentials:
   - Data: User passwords (hashed), session tokens, API keys
   - Storage: Auth0 (SaaS), Secrets Manager, Application memory
   - Sensitivity: HIGH (credentials = keys to PHI)
   - Threat: Credential theft, session hijacking, brute force

3. Application Availability:
   - Service: Customer portal uptime
   - Dependency: AWS infrastructure, third-party Auth0
   - Business Impact: Revenue loss, regulatory penalties if clinical data inaccessible
   - Threat: DDoS, infrastructure failure, dependency failure

4. [Additional assets...]
```

**Threat Actors**:
```
Likely Threat Actors (by priority):

1. External Attackers (Opportunistic):
   - Motivation: Financial gain (PHI for resale, ransomware)
   - Sophistication: LOW to MEDIUM (automated scanners, known exploits)
   - Likely TTPs: SQLi, XSS, credential stuffing, vulnerability exploitation
   - Priority: HIGH (internet-facing = high exposure)

2. Insider Threats:
   - Motivation: Curiosity, malice, negligence
   - Sophistication: VARIES (authorized access, knows environment)
   - Likely TTPs: Data exfiltration, privilege abuse, credential sharing
   - Priority: MEDIUM (healthcare has elevated insider risk)

3. Advanced Persistent Threat (Nation-State/Organized Crime):
   - Motivation: Espionage, large-scale data theft
   - Sophistication: HIGH (custom exploits, social engineering, supply chain)
   - Likely TTPs: Spearphishing, zero-days, long-term persistence
   - Priority: MEDIUM (healthcare targeting observed, but we're not high-value target)

4. [Additional threat actors based on context...]
```

**Attack Scenarios** (STRIDE Analysis):

| Threat Type | Scenario | Asset at Risk | Likelihood | Impact | Priority |
|-------------|----------|---------------|------------|--------|----------|
| **Spoofing** | Attacker bypasses MFA, accesses account | PHI data | MEDIUM | CRITICAL | HIGH |
| **Tampering** | SQLi modifies patient records | Data integrity | MEDIUM | HIGH | HIGH |
| **Repudiation** | Admin action not logged, no audit trail | Accountability | LOW | MEDIUM | MEDIUM |
| **Info Disclosure** | Insecure API exposes PHI without auth | PHI confidentiality | HIGH | CRITICAL | CRITICAL |
| **Denial of Service** | DDoS overwhelms application | Availability | MEDIUM | HIGH | MEDIUM |
| **Elevation of Privilege** | API vuln allows user→admin escalation | All assets | LOW | CRITICAL | HIGH |

**Attack Surface Map**:
```
Internet-Exposed:
- CloudFront (CDN) → React Frontend
- Application Load Balancer → API (ECS Fargate containers)
- Auth0 Login Pages (third-party)

Internal (VPC):
- ECS tasks running Node.js API
- RDS PostgreSQL database (private subnets)
- Secrets Manager (API access via IAM)

Trust Boundaries:
- Internet ←→ CloudFront/ALB (primary boundary)
- ALB ←→ ECS Tasks (internal, but user-controlled input flows here)
- ECS ←→ RDS (database access, credentials-based trust)
- Application ←→ Auth0 (federated trust, token-based)
```

---

**PHASE 2: DEFENSE-IN-DEPTH ASSESSMENT**

Evaluate security controls across layers:

**Layer 1: Network Security**

```
PERIMETER DEFENSES:

✅ IMPLEMENTED:
- AWS Security Groups: Inbound restricted to 443 from Internet (ALB), 5432 only from ECS security group (RDS)
- Network ACLs: Default VPC NACLs, not customized
- Private Subnets: RDS in private subnets (no direct internet access)
- NAT Gateway: ECS tasks access internet via NAT for updates

⚠️ GAPS:
- No WAF (Web Application Firewall): Application exposed without L7 protection
  - Risk: No defense against OWASP Top 10 (SQLi, XSS), no rate limiting, no geo-blocking
  - Recommendation: Deploy AWS WAF with managed rule sets (OWASP, known bad inputs)
  
- No DDoS Protection (AWS Shield Advanced): Only default Shield Standard
  - Risk: Volumetric DDoS could overwhelm, no cost protection, limited visibility
  - Recommendation: Consider Shield Advanced for CRITICAL apps ($3K/month, but includes DDoS response team)

- Overly Permissive Security Groups: Some SGs allow 0.0.0.0/0 on ports other than 443
  - Risk: Unintended exposure if misconfigured services
  - Recommendation: Apply least privilege, restrict to specific IP ranges or security groups

NETWORK SEGMENTATION:

✅ IMPLEMENTED:
- Application tier (ECS) separated from data tier (RDS) via security groups
- RDS in private subnets (not internet-routable)

⚠️ GAPS:
- Single VPC: No segmentation between prod/staging/dev environments
  - Risk: Compromise of dev/staging could pivot to production
  - Recommendation: Separate VPCs per environment with VPC peering/PrivateLink as needed

- No micro-segmentation: All ECS tasks in same security group
  - Risk: Lateral movement between containers if one compromised
  - Recommendation: If using microservices, isolate each service with dedicated SG

MONITORING:

✅ IMPLEMENTED:
- VPC Flow Logs enabled
- CloudWatch alarms for some network metrics

⚠️ GAPS:
- Flow Logs not analyzed: Data collected but no alerting on anomalies
  - Risk: Won't detect reconnaissance, data exfiltration, or unusual traffic
  - Recommendation: Send flow logs to SIEM or use AWS GuardDuty for automated analysis
```

**Layer 2: Application Security**

```
INPUT VALIDATION:

⚠️ CRITICAL GAPS IDENTIFIED:

- API Endpoints: Input validation inconsistent across endpoints
  - Risk: SQL injection, NoSQL injection, command injection possible
  - Example: /api/search endpoint accepts user input without parameterized queries
  - Recommendation: 
    1. IMMEDIATE: Code review all user input handling
    2. Implement parameterized queries/prepared statements everywhere (blocks SQLi)
    3. Input validation library (Joi, Validator.js) with allowlisting approach
    4. Automated SAST scanning in CI/CD to catch future issues

- File Upload: No file type restriction or malware scanning
  - Risk: Malicious file upload → RCE, XSS, or malware hosting
  - Recommendation:
    1. Allowlist file types by extension AND magic bytes
    2. Scan uploads with antivirus (ClamAV or cloud service)
    3. Store uploads outside webroot, serve via separate domain (prevent XSS)
    4. Implement file size limits

OUTPUT ENCODING:

⚠️ GAPS:
- React Frontend: Relying on React XSS protections, but dangerous patterns observed
  - Risk: XSS via dangerouslySetInnerHTML or unsanitized props
  - Example: User profile renders HTML from API without sanitization
  - Recommendation:
    1. Code review all dangerouslySetInnerHTML usage (eliminate if possible)
    2. Use DOMPurify library for HTML sanitization if HTML rendering required
    3. Content Security Policy (CSP) header to mitigate XSS impact

AUTHENTICATION & AUTHORIZATION:

✅ IMPLEMENTED:
- MFA Available: Auth0 supports MFA (SMS, authenticator app)
- OAuth 2.0/OIDC: Modern, secure authentication protocol
- Session Management: JWT tokens with reasonable expiry (1 hour)

⚠️ GAPS:
- MFA Not Enforced: Optional for users, not required
  - Risk: Credential stuffing, phishing bypasses single-factor
  - Recommendation: ENFORCE MFA for all accounts, especially admins

- Authorization Logic: RBAC implemented but authorization checks inconsistent in API
  - Risk: Horizontal privilege escalation (User A accesses User B's records)
  - Example: /api/patient/:id endpoint doesn't validate requesting user owns patient ID
  - Recommendation:
    1. CRITICAL: Audit all API endpoints for authorization flaws (IDOR vulnerabilities)
    2. Implement consistent authorization middleware checking ownership/permissions
    3. Principle of least privilege: Users only access their own data unless admin

- Token Storage: JWT stored in localStorage
  - Risk: XSS can steal token → account takeover
  - Recommendation: Use httpOnly cookies for token storage (XSS can't access), with SameSite=Strict

SESSION MANAGEMENT:

⚠️ GAPS:
- No Token Revocation: JWT-based, no revocation mechanism
  - Risk: If credential compromised, can't terminate sessions remotely
  - Recommendation: Implement token revocation (Redis allowlist/blocklist) or reduce token lifetime + refresh token pattern

- No Session Monitoring: Can't detect concurrent sessions from different IPs (account sharing or compromise)
  - Recommendation: Log login events with IP/geolocation, alert on anomalies

CRYPTOGRAPHY:

✅ IMPLEMENTED:
- TLS 1.2+ (CloudFront, ALB): HTTPS enforced
- Password Hashing: Auth0 handles (bcrypt default)
- PHI Encryption at Rest: RDS encryption enabled (AES-256)

⚠️ GAPS:
- API Keys in Code: Found hardcoded AWS Access Keys in repository history
  - Risk: CRITICAL - Keys exposed in Git history, even if removed from current version
  - Recommendation:
    1. IMMEDIATE: Rotate all potentially exposed keys
    2. Scan git history with truffleHog, git-secrets
    3. Use AWS Secrets Manager + IAM roles (no hardcoded credentials)
    4. Git pre-commit hooks to block secrets

- No Field-Level Encryption: PHI in database encrypted at disk level, but readable by application/DBAs
  - Risk: Insider threat, database compromise exposes plaintext PHI
  - Recommendation: Consider application-layer encryption for most sensitive fields (SSN, medical history) with key management

LOGGING & MONITORING:

✅ IMPLEMENTED:
- Application logs to ELK stack
- CloudWatch alarms on HTTP errors (5xx)

⚠️ GAPS:
- Insufficient Security Event Logging: Not logging authentication events, authorization failures, sensitive data access
  - Risk: Can't detect attacks, no forensics capability
  - Recommendation:
    1. Log: All authentication (success/failure), authorization decisions, data access (who accessed which patient record)
    2. Centralize in SIEM
    3. Alerts on suspicious patterns (repeated auth failures, privilege escalation attempts, unusual data access)

- No Log Integrity: Logs can be modified/deleted by application or attackers
  - Recommendation: Forward logs to immutable storage (AWS S3 with object lock) or SIEM that attacker can't access
```

**Layer 3: Data Security**

```
DATA CLASSIFICATION:

✅ IMPLEMENTED:
- PHI identified and labeled in data model

⚠️ GAPS:
- No Data Loss Prevention (DLP): Can't detect/prevent unauthorized PHI exfiltration
  - Risk: Insider exfiltrates PHI via API, email, or database export
  - Recommendation: Implement DLP monitoring (AWS Macie for S3, database activity monitoring for RDS)

ENCRYPTION:

✅ IMPLEMENTED:
- At Rest: RDS encryption (AWS KMS)
- In Transit: TLS everywhere (CloudFront, ALB, internal)

⚠️ GAPS:
- Encryption Key Management: Using AWS-managed keys (aws/rds), not customer-managed
  - Risk: Less control over key rotation, access
  - Recommendation: Use customer-managed KMS keys (CMK) with key policies restricting access

DATA RETENTION:

⚠️ GAPS:
- No Retention Policy: Data retained indefinitely
  - Risk: Compliance violation (GDPR right to erasure, HIPAA minimum necessary), increased breach impact (more data = more risk)
  - Recommendation:
    1. Define retention policy (e.g., 7 years per HIPAA, then secure deletion)
    2. Implement automated data lifecycle (archive old data, purge after retention period)

BACKUP & RECOVERY:

✅ IMPLEMENTED:
- RDS automated backups (7-day retention)
- Daily manual snapshots

⚠️ GAPS:
- Backup Encryption: Snapshots encrypted, but backup restoration not tested
  - Risk: Backups may be unusable in emergency (untested = untrustworthy)
  - Recommendation: Quarterly DR drills (restore from backup to separate environment, validate functionality)

- No Off-Site Backup: All backups in same AWS region
  - Risk: Regional failure = data loss
  - Recommendation: Cross-region backup replication for CRITICAL data
```

**Layer 4: Identity & Access Management**

```
IDENTITY MANAGEMENT:

✅ IMPLEMENTED:
- Centralized Identity: Auth0 for customer authentication
- AWS IAM for infrastructure access

⚠️ GAPS:
- No Privileged Access Management (PAM): Admins use static AWS IAM users
  - Risk: Credentials long-lived, no MFA enforcement for AWS access, no session recording
  - Recommendation:
    1. ENFORCE MFA on all AWS IAM users (especially admins)
    2. Use AWS SSO or third-party PAM (BeyondTrust, CyberArk) for temporary, just-in-time admin access
    3. Eliminate long-lived access keys (use IAM roles instead)

LEAST PRIVILEGE:

⚠️ GAPS:
- IAM Roles Overly Permissive: ECS task role has broad S3 permissions (s3:*)
  - Risk: Container compromise = access to all S3 buckets
  - Recommendation:
    1. Audit all IAM policies with AWS Access Analyzer
    2. Apply least privilege (specific actions on specific resources)
    3. Example: Replace s3:* with s3:GetObject on specific bucket/prefix

- Database Permissions: Application uses single DB user with full permissions (CREATE, DROP, etc.)
  - Risk: SQLi can DROP tables or modify schema
  - Recommendation: Application user should only have SELECT, INSERT, UPDATE, DELETE on specific tables (not DDL)

ACCESS REVIEWS:

⚠️ GAPS:
- No Periodic Access Review: User accounts never reviewed for removal
  - Risk: Dormant accounts (ex-employees?) remain active
  - Recommendation:
    1. Quarterly access review (disable unused accounts)
    2. Automated: Integrate with HR system (offboarding triggers account deactivation)
```

---

**PHASE 3: ATTACK PATH ANALYSIS**

Map realistic attack scenarios:

**Critical Attack Path 1: External Attacker → PHI Breach**

```
Attack Chain:

1. Reconnaissance:
   - Attacker scans application (Nmap, Burp)
   - Identifies technology stack (React, Node.js, AWS)
   - Maps API endpoints (/api/search, /api/patient/:id)

2. Initial Access:
   - SQLi in /api/search endpoint (identified in Phase 2)
   - Attacker injects: ' OR '1'='1 --
   - Backend query: SELECT * FROM patients WHERE name = '' OR '1'='1' --'
   - Result: Entire patients table dumped

3. Data Exfiltration:
   - Attacker scripts automated extraction via SQLi
   - Downloads PHI for entire patient population (thousands of records)
   - No DLP or rate limiting detects exfiltration

4. Impact:
   - HIPAA breach notification required (>500 individuals)
   - Regulatory fines: $100-$1.5M per HIPAA violation category
   - Reputational damage, patient trust loss
   - Potential class-action lawsuit

Current Defenses (Insufficient):
- ❌ No WAF to block SQLi
- ❌ Input validation not implemented
- ❌ No parameterized queries
- ❌ No DLP or anomaly detection

Recommended Mitigations (Defense-in-Depth):
- 🛡️ WAF with SQLi rule set (blocks common SQLi patterns)
- 🛡️ Code fix: Parameterized queries (prevents SQLi entirely)
- 🛡️ Input validation (allowlist characters for search)
- 🛡️ Database activity monitoring (alerts on large data exports)
- 🛡️ Rate limiting (prevents bulk extraction even if SQLi exists)
```

**Critical Attack Path 2: Insider Threat → Data Misuse**

```
Attack Chain:

1. Authorized Access:
   - Insider (employee, contractor) has legitimate login
   - MFA not enforced, single-factor authentication

2. Abuse of Privilege:
   - Insider accesses API directly (bypassing UI rate limits)
   - Writes script to enumerate all patient IDs (/api/patient/1, /api/patient/2, ...)
   - Authorization bug (Phase 2): API doesn't validate user owns patient record (IDOR)

3. Data Collection:
   - Insider downloads PHI for patients they have no business accessing
   - Logs show access, but no alerting on unusual patterns (e.g., accessing hundreds of records)

4. Exfiltration:
   - Insider copies data to personal device or emails to personal account
   - No DLP prevents egress of PHI

5. Impact:
   - Privacy violation, potential identity theft for patients
   - Regulatory breach, insider criminally prosecuted
   - Organization faces fines and reputation damage

Current Defenses (Insufficient):
- ❌ Authorization not enforced per-record (IDOR vulnerability)
- ❌ No monitoring for unusual access patterns
- ❌ No DLP on data egress
- ❌ MFA not enforced (credential theft easier)

Recommended Mitigations:
- 🛡️ Fix IDOR: Validate user ownership on every API call
- 🛡️ Implement UEBA (User/Entity Behavior Analytics) - alert on abnormal access (e.g., accessing >50 records in 10 minutes)
- 🛡️ DLP monitoring on database, API, email
- 🛡️ Enforce MFA (harder to steal credentials)
- 🛡️ Break-glass audit: Any access to records outside user's normal scope requires justification and manager approval
```

**Critical Attack Path 3: Supply Chain Compromise → Backend Takeover**

```
Attack Chain:

1. Third-Party Compromise:
   - Attacker compromises npm package used by application
   - Package update includes malicious code (supply chain attack)

2. Malicious Package Deployment:
   - Developer runs npm update, pulls compromised package
   - CI/CD pipeline builds and deploys to production
   - No dependency vulnerability scanning caught this

3. Code Execution:
   - Malicious code executes in ECS container
   - Establishes reverse shell to attacker C2
   - Container has overly permissive IAM role (s3:*, secretsmanager:GetSecretValue)

4. Privilege Escalation:
   - Attacker reads secrets from Secrets Manager (DB credentials, API keys)
   - Accesses RDS directly from container (security group allows)

5. Impact:
   - Full database access (read, modify, delete)
   - Potential ransomware (encrypt DB, demand payment)
   - Long-term persistence (attacker maintains backdoor)

Current Defenses (Insufficient):
- ❌ No Software Composition Analysis (SCA) in CI/CD
- ❌ No dependency allowlisting or integrity checking
- ❌ Overly permissive IAM roles
- ❌ Container can access RDS (should be network-segmented for some architectures)

Recommended Mitigations:
- 🛡️ SCA tools (Snyk, Dependabot, npm audit) in CI/CD
- 🛡️ Dependency pinning + integrity checks (package-lock.json with SRI hashes)
- 🛡️ Least privilege IAM (container role only access Secrets Manager for specific secrets needed)
- 🛡️ Container runtime security (Falco, AWS GuardDuty for ECS) - detect anomalous behavior
- 🛡️ Network segmentation with bastion pattern (app doesn't connect directly to DB, goes through bastion/proxy)
```

---

**PHASE 4: COMPLIANCE GAP ANALYSIS**

Assess compliance with required frameworks:

**HIPAA Security Rule Compliance**

```
| HIPAA Requirement | Status | Gap | Priority |
|-------------------|--------|-----|----------|
| **Administrative Safeguards** |
| Security Management Process | ⚠️ PARTIAL | No risk assessment documented in last 12 months | HIGH |
| Workforce Security | ⚠️ PARTIAL | No background checks for contractors, termination process informal | MEDIUM |
| Information Access Management | ❌ NOT MET | No formal access authorization process, no periodic review | HIGH |
| Security Awareness Training | ✅ MET | Annual security training provided | - |
| Security Incident Procedures | ⚠️ PARTIAL | Incident response plan exists but not tested | MEDIUM |
| **Physical Safeguards** |
| Facility Access Controls | ✅ MET | Cloud-based (AWS), physical security is AWS responsibility | - |
| Workstation Security | ⚠️ PARTIAL | No policy on remote work security (home office not secured) | MEDIUM |
| **Technical Safeguards** |
| Access Control | ⚠️ PARTIAL | No emergency access procedure, MFA not enforced | HIGH |
| Audit Controls | ❌ NOT MET | Insufficient logging of PHI access, no tamper-proof audit logs | CRITICAL |
| Integrity | ✅ MET | Checksums, encryption protect data integrity | - |
| Transmission Security | ✅ MET | TLS everywhere | - |

CRITICAL COMPLIANCE GAPS:

1. Audit Controls (§164.312(b)):
   - Requirement: "Implement hardware, software, and/or procedural mechanisms that record and examine activity in information systems that contain or use ePHI"
   - Gap: Not logging who accessed which patient records, when, from where
   - Impact: Cannot demonstrate HIPAA compliance in audit, cannot investigate potential breaches
   - Recommendation: 
     1. Implement comprehensive audit logging (authentication, PHI access, modifications)
     2. Immutable log storage
     3. SIEM with HIPAA-specific reports
     4. Quarterly log review process
   - Effort: MEDIUM (2-4 weeks development + ongoing process)
   - Cost: ~$20K for SIEM + logging infrastructure

2. Information Access Management (§164.308(a)(4)):
   - Requirement: "Implement policies and procedures for authorizing access to ePHI"
   - Gap: No formal access request/approval process, no periodic access reviews
   - Impact: Cannot demonstrate least privilege, insider threat risk
   - Recommendation:
     1. Document access authorization policy
     2. Implement workflow (ServiceNow, Jira) for access requests with manager approval
     3. Quarterly access reviews (disable unused accounts)
   - Effort: LOW (1-2 weeks for process, tooling may already exist)
   - Cost: Minimal (process documentation)

3. Access Control - MFA (§164.312(a)(2)(i)):
   - Requirement: "Assign a unique name and/or number for identifying and tracking user identity"
   - Gap: MFA available but not enforced (single-factor allowed)
   - Impact: Weak authentication, credential theft risk
   - Recommendation: Enforce MFA for all accounts (no exceptions)
   - Effort: LOW (configuration change in Auth0)
   - Cost: Minimal (existing MFA infrastructure)
```

**SOC 2 Type II Readiness**

```
| TSC | Control | Status | Gap | Priority |
|-----|---------|--------|-----|----------|
| CC6.1 | Logical & Physical Access | ⚠️ PARTIAL | MFA not enforced, no PAM | HIGH |
| CC6.6 | Logical Access - Removal | ❌ NOT MET | No offboarding process for account deactivation | HIGH |
| CC7.2 | System Monitoring | ⚠️ PARTIAL | Monitoring exists but gaps in security event coverage | MEDIUM |
| CC7.4 | Response to Incidents | ⚠️ PARTIAL | IR plan not tested, no tabletop exercises | MEDIUM |
| CC8.1 | Change Management | ❌ NOT MET | No formal change control for infrastructure changes | MEDIUM |

[Similar detailed gap analysis...]
```

---

**PHASE 5: RISK SCORING AND PRIORITIZATION**

Quantify risk and prioritize remediation:

**Risk Calculation Framework**:

```
Risk = Likelihood × Impact × Exploitability

Likelihood: How probable is exploitation?
- HIGH (3): Common attack vector, easy to find vulnerability
- MEDIUM (2): Requires some reconnaissance or conditions
- LOW (1): Rare, requires significant attacker capability

Impact: What's the damage if exploited?
- CRITICAL (4): Full system compromise, massive data breach, business shutdown
- HIGH (3): Significant data breach, major service disruption
- MEDIUM (2): Limited data exposure, temporary service impact
- LOW (1): Minimal damage

Exploitability: How easy to exploit?
- HIGH (3): No authentication required, automated exploit available
- MEDIUM (2): Authentication required but weak, manual exploitation
- LOW (1): Complex exploit, requires multiple prerequisites
```

**Risk Register**:

| # | Finding | Likelihood | Impact | Exploit | Risk Score | Priority |
|---|---------|------------|--------|---------|------------|----------|
| 1 | SQL Injection in /api/search | HIGH (3) | CRITICAL (4) | HIGH (3) | 36 | CRITICAL |
| 2 | IDOR - Horizontal Privilege Escalation | HIGH (3) | HIGH (3) | HIGH (3) | 27 | CRITICAL |
| 3 | No WAF Protection | HIGH (3) | HIGH (3) | MEDIUM (2) | 18 | HIGH |
| 4 | MFA Not Enforced | MEDIUM (2) | HIGH (3) | MEDIUM (2) | 12 | HIGH |
| 5 | Hardcoded Secrets in Git History | HIGH (3) | CRITICAL (4) | LOW (1) | 12 | HIGH |
| 6 | Insufficient Audit Logging | MEDIUM (2) | MEDIUM (2) | MEDIUM (2) | 8 | MEDIUM |
| 7 | Overly Permissive IAM Roles | MEDIUM (2) | HIGH (3) | LOW (1) | 6 | MEDIUM |
| 8 | No DLP Monitoring | LOW (1) | HIGH (3) | MEDIUM (2) | 6 | MEDIUM |
| 9 | No Backup Testing | LOW (1) | HIGH (3) | LOW (1) | 3 | LOW |
| [Continue...] | [...] | [...] | [...] | [...] | [...] | [...] |
```

---

OUTPUT FORMAT:

## Security Architecture Review: [SYSTEM_NAME]

**Review Classification**: [INTERNAL USE / CONFIDENTIAL]
**Review Date**: [DATE]
**Reviewer**: [Your role/name]
**Review Type**: [COMPREHENSIVE / FOCUSED]
**Distribution**: [Intended stakeholders]

---

### EXECUTIVE SUMMARY

**System Reviewed**: [Name and business purpose]

**Overall Security Posture**: [STRONG / ADEQUATE / WEAK / CRITICAL CONCERNS]

**Key Findings**:
1. [Most critical finding with risk level]
2. [Second most critical]
3. [Third most critical]

**Critical Risks Identified**: [NUMBER]
- CRITICAL Severity: [COUNT] findings requiring immediate attention
- HIGH Severity: [COUNT] findings requiring near-term remediation
- MEDIUM Severity: [COUNT] findings for planned improvement
- LOW Severity: [COUNT] observations for consideration

**Compliance Status**:
- HIPAA: [COMPLIANT / GAPS EXIST / NON-COMPLIANT] - [Brief summary]
- SOC 2: [READY / GAPS EXIST / NOT READY] - [Brief summary]

**Recommendation Summary**:
- Immediate Actions (0-30 days): [COUNT] findings
- Short-Term (1-3 months): [COUNT] findings
- Long-Term (3-12 months): [COUNT] findings

**Estimated Remediation Investment**:
- Immediate: $[AMOUNT] + [PERSON-WEEKS] effort
- Total: $[AMOUNT] + [PERSON-WEEKS] effort over 12 months

**Go/No-Go Recommendation**:
[APPROVE FOR PRODUCTION / APPROVE WITH CONDITIONS / DO NOT APPROVE]

Conditions for approval:
1. [Critical finding 1] must be remediated before launch
2. [Critical finding 2] must be remediated before launch
3. [Plan in place for High-severity findings within 90 days]

---

### REVIEW SCOPE AND METHODOLOGY

**System Context**:
[Your architecture review scope details]

**Review Approach**:
[Your assessment method and time allocated]

**Assumptions and Limitations**:
- Review based on documentation as of [DATE]
- No penetration testing performed (architecture review only)
- Threat model assumes [specific threat actors]
- [Other limitations]

---

### THREAT MODEL

**Assets**:
[Your Phase 1 critical assets]

**Threat Actors**:
[Your Phase 1 threat actor profiles with priority]

**Attack Scenarios** (STRIDE):
[Your Phase 1 STRIDE table]

**Attack Surface**:
[Your Phase 1 attack surface map]

---

### DEFENSE-IN-DEPTH ASSESSMENT

**Layer 1: Network Security**
[Your Phase 2 Network Security assessment with ✅ implemented and ⚠️ gaps]

**Layer 2: Application Security**
[Your Phase 2 Application Security assessment]

**Layer 3: Data Security**
[Your Phase 2 Data Security assessment]

**Layer 4: Identity & Access Management**
[Your Phase 2 IAM assessment]

---

### CRITICAL ATTACK PATHS

**Attack Path 1**: [Name]
[Your Phase 3 attack chain for critical path 1]

**Attack Path 2**: [Name]
[Your Phase 3 attack chain for critical path 2]

**Attack Path 3**: [Name]
[Your Phase 3 attack chain for critical path 3]

---

### COMPLIANCE ANALYSIS

**HIPAA Compliance**:
[Your Phase 4 HIPAA gap analysis table and detailed critical gaps]

**SOC 2 Readiness**:
[Your Phase 4 SOC 2 gap analysis]

**Other Regulations**:
[If applicable: GDPR, PCI-DSS, state privacy laws, etc.]

---

### RISK REGISTER

[Your Phase 5 risk calculation framework and detailed risk register table]

**Risk Distribution**:
```
CRITICAL (36+):     ██████ [COUNT] findings
HIGH (18-35):       ████████ [COUNT] findings  
MEDIUM (6-17):      ██████████ [COUNT] findings
LOW (1-5):          ████ [COUNT] findings
```

---

### DETAILED FINDINGS AND RECOMMENDATIONS

**Format**: Each finding includes:
- Finding ID
- Title
- Severity (CRITICAL / HIGH / MEDIUM / LOW)
- Description
- Risk Explanation
- Affected Components
- Recommendation
- Implementation Guidance
- Effort Estimate
- Cost Estimate

---

**FINDING #1: SQL Injection Vulnerability in Search API**

**Severity**: CRITICAL (Risk Score: 36)

**Description**:
The /api/search endpoint accepts user input (search terms) and directly concatenates it into SQL queries without parameterization or input validation. Testing confirmed SQL injection is possible:

```
Request: GET /api/search?query=' OR '1'='1' --
Response: Returns all patient records (full PHI database dump)
```

**Risk Explanation**:
- Attacker can extract entire patient database (HIPAA breach)
- Attacker can modify or delete data (integrity compromise)
- Attacker can escalate to OS command execution (depending on database permissions)
- Likelihood: HIGH (internet-facing, easy to discover and exploit)
- Impact: CRITICAL (full data breach, compliance violation, regulatory fines)

**Affected Components**:
- `/api/search` endpoint (Node.js API)
- PostgreSQL database (all tables accessible)
- Patient records (all PHI at risk)

**Recommendation**:

**IMMEDIATE** (Deploy within 24-48 hours):
1. Take /api/search endpoint offline until fixed (if business-critical, add temporary WAF rule to block SQLi patterns)
2. Review all other API endpoints for similar vulnerabilities

**SHORT-TERM** (Complete within 1 week):
1. Implement parameterized queries/prepared statements for ALL database interactions
   ```javascript
   // VULNERABLE CODE:
   const query = `SELECT * FROM patients WHERE name = '${userInput}'`;
   
   // SECURE CODE:
   const query = 'SELECT * FROM patients WHERE name = $1';
   const result = await pool.query(query, [userInput]);
   ```

2. Input validation with allowlisting:
   ```javascript
   // Only allow alphanumeric, spaces, hyphens
   if (!/^[a-zA-Z0-9\s\-]+$/.test(userInput)) {
     return res.status(400).json({error: "Invalid search term"});
   }
   ```

3. Deploy Web Application Firewall (AWS WAF) with OWASP Core Rule Set as defense-in-depth
4. Integrate SAST tool (SonarQube, Checkmarx) into CI/CD to prevent future SQLi

**Implementation Guidance**:
- Use ORM/query builder (Sequelize, Knex.js) to enforce parameterization
- All user input is untrusted: URL params, POST body, headers, cookies
- Test fix with SQLi payloads before deploying
- Monitor database error logs for exploitation attempts

**Effort**: 40 hours (1 week for thorough remediation across entire codebase)
**Cost**: $0 (internal engineering time)
**Owner**: Development Team Lead
**Target**: Within 7 days of report

---

**FINDING #2: Insecure Direct Object Reference (IDOR) - Authorization Bypass**

**Severity**: CRITICAL (Risk Score: 27)

**Description**:
API endpoints that return patient-specific data (e.g., /api/patient/:id, /api/records/:recordId) do not validate that the authenticated user has permission to access the requested resource. Testing confirmed horizontal privilege escalation:

```
User A (authenticated, patient ID: 123) requests:
GET /api/patient/456 (User B's record)

Response: Returns User B's PHI (full patient record)
```

Any authenticated user can access ANY patient's records by enumerating IDs.

**Risk Explanation**:
- Privacy violation: Users can access other patients' PHI
- HIPAA breach: Unauthorized disclosure
- Insider threat: Malicious employee can exfiltrate entire database
- Likelihood: HIGH (any authenticated user, easy to discover)
- Impact: HIGH to CRITICAL (PHI breach, regulatory penalties)

**Affected Components**:
- All patient-specific API endpoints
- Authorization middleware (insufficient validation)

**Recommendation**:

**IMMEDIATE** (Deploy within 48 hours):
1. Implement strict authorization check on every API endpoint accessing patient data:
   ```javascript
   // Middleware or per-route check:
   async function validateOwnership(req, res, next) {
     const requestedPatientId = req.params.id;
     const authenticatedUserId = req.user.id; // From JWT
     
     // Check if user owns this patient record or is admin
     if (req.user.role !== 'admin' && requestedPatientId !== authenticatedUserId) {
       return res.status(403).json({error: "Forbidden: Access denied"});
     }
     next();
   }
   
   app.get('/api/patient/:id', validateOwnership, getPatientHandler);
   ```

2. Audit ALL API endpoints for authorization flaws:
   - Create spreadsheet of every endpoint
   - Document expected authorization behavior
   - Test each with non-owner users

3. Implement User Behavior Analytics (UBA):
   - Alert on user accessing >10 patient records in 1 hour (unusual)
   - Alert on user accessing records outside normal geographic region

**Implementation Guidance**:
- Use consistent authorization middleware across all routes
- Default-deny: Require explicit authorization for every endpoint
- Test with multiple user roles and edge cases
- Consider attribute-based access control (ABAC) if permissions are complex

**Effort**: 60 hours (1.5 weeks for comprehensive audit and implementation)
**Cost**: $0 (internal engineering time) + potential UBA tooling ($5K-$20K/year)
**Owner**: Development Team Lead + Security Engineer
**Target**: Within 14 days of report

---

[Continue with FINDING #3 through #N in same detailed format...]

---

### REMEDIATION ROADMAP

**Immediate Actions (0-30 days)** - CRITICAL severity, blocking launch:

| Finding | Action | Owner | Target Date | Status |
|---------|--------|-------|-------------|--------|
| #1: SQL Injection | Parameterized queries, WAF deployment | Dev Lead | [DATE] | NOT STARTED |
| #2: IDOR | Authorization validation | Dev Lead + SecEng | [DATE] | NOT STARTED |
| #5: Hardcoded Secrets | Rotate keys, use Secrets Manager | DevOps | [DATE] | NOT STARTED |
| #3: No WAF | Deploy AWS WAF with OWASP rules | DevOps | [DATE] | NOT STARTED |

**Estimated Effort**: 200 hours (~5 person-weeks)
**Estimated Cost**: $15K (WAF + tooling)

---

**Short-Term Actions (1-3 months)** - HIGH severity:

| Finding | Action | Owner | Target Date | Status |
|---------|--------|-------|-------------|--------|
| #4: MFA Not Enforced | Enable MFA enforcement in Auth0 | DevOps | [DATE] | - |
| #6: Audit Logging Gaps | Implement comprehensive audit logging | Dev + SecEng | [DATE] | - |
| #7: Overly Permissive IAM | IAM policy remediation | DevOps | [DATE] | - |
| [Continue...] | [...] | [...] | [...] | - |

**Estimated Effort**: 300 hours (~7.5 person-weeks)
**Estimated Cost**: $25K (SIEM, tooling, potential consulting)

---

**Long-Term Improvements (3-12 months)** - MEDIUM/LOW severity + strategic enhancements:

| Finding | Action | Owner | Target Date | Status |
|---------|--------|-------|-------------|--------|
| #9: No Backup Testing | Quarterly DR drills | Operations | [DATE] | - |
| Architecture: Micro-segmentation | VPC redesign for env separation | Cloud Architect | [DATE] | - |
| Strategic: PAM Implementation | Deploy privileged access mgmt | Security Architect | [DATE] | - |
| [Continue...] | [...] | [...] | [...] | - |

**Estimated Effort**: 800 hours (~20 person-weeks)
**Estimated Cost**: $150K (architecture changes, PAM tooling, consulting)

---

### SUCCESS METRICS

**How to measure remediation progress**:

1. **Critical Findings Closure**: 0 CRITICAL findings remaining (currently: [COUNT])
   - Measurement: Re-test each CRITICAL finding after remediation
   - Target: 100% closure before production launch

2. **Vulnerability Remediation Velocity**: 
   - HIGH findings: Close within 90 days (currently: [COUNT] open)
   - MEDIUM findings: Close within 6 months
   - Target: 90% closure rate within SLA

3. **Compliance Status**:
   - HIPAA: 100% of required controls implemented
   - SOC 2: Pass Type II audit without findings
   - Measurement: Compliance checklist completion, audit results

4. **Security Incident Rate**:
   - Baseline: [Current incident rate if known]
   - Target: <[acceptable rate] incidents per quarter
   - Measurement: Incident tracking in SIEM/ticketing system

5. **Audit Log Coverage**:
   - Baseline: [Current log coverage %]
   - Target: 100% of PHI access logged
   - Measurement: Audit log analysis tool

---

### NEXT STEPS

**Immediate** (This week):
1. [ ] Executive review and approval of remediation roadmap
2. [ ] Assign owners to each CRITICAL finding
3. [ ] Establish weekly remediation status meeting
4. [ ] Allocate budget for immediate tooling needs ($15K)

**Short-Term** (Next 30 days):
1. [ ] Complete all CRITICAL finding remediation
2. [ ] Re-test and validate fixes
3. [ ] Update architecture documentation with changes
4. [ ] Begin HIGH severity finding remediation

**Long-Term** (3-12 months):
1. [ ] Quarterly architecture security reviews
2. [ ] Annual penetration testing
3. [ ] Continuous improvement based on threat landscape changes

---

### APPENDICES

**Appendix A: Detailed Technical Findings**
[Full technical detail for each finding, including exploitation proof-of-concepts if applicable]

**Appendix B: Architecture Diagrams**
[Current state architecture with security control overlays]

**Appendix C: Compliance Mapping**
[Detailed mapping of findings to compliance requirements]

**Appendix D: Risk Calculation Methodology**
[Full explanation of risk scoring approach]

**Appendix E: References**
- OWASP Top 10 (2021)
- MITRE ATT&CK Framework
- NIST Cybersecurity Framework
- CIS Controls v8
- [Industry-specific references]

---

**Report Prepared By**: [Security Architecture Team]
**Review Frequency**: [Quarterly or after major architecture changes]
**Next Review Date**: [DATE]
**Questions/Feedback**: [Contact information]

---

CRITICAL CONSTRAINTS:
- Recommendations must be technically feasible with stated constraints (budget, team, timeline)
- Risk scores must be justified with evidence (not arbitrary ratings)
- Remediation estimates must be realistic (include testing, documentation, deployment time)
- Compliance analysis must reference specific regulatory requirements (not generic statements)
- Attack paths must be realistic for identified threat actors
- If assumptions required, note: "[Based on documentation review; validation via testing recommended]"

TONE:
- Professional and constructive (identify problems, provide solutions)
- Risk-focused (explain impact, not just technical details)
- Actionable (clear recommendations with implementation guidance)
- Balanced (acknowledge what's done well, focus on gaps)

⚠️ ARCHITECTURE REVIEW REMINDER:
Security architecture reviews are preventive measures:
1. Conduct reviews before production launch (shift-left security)
2. Update reviews quarterly or after major changes
3. Track remediation progress with measurable metrics
4. Re-test after remediation to validate fixes
5. Maintain architecture documentation as living document
6. Security architecture evolves with threat landscape - review is never "done"

Architecture reviews prevent expensive post-production security incidents.
```

**🏢 Enterprise Tool Additions:**
- Include actual system names, URLs, and architecture diagrams
- Reference specific AWS account IDs, VPC IDs, security group IDs
- Provide real code snippets showing vulnerabilities (sanitized appropriately)
- Include actual compliance framework versions and requirement references
- Name specific team members as finding owners
- Reference actual budget allocation and cost centers
- Include real timeline dates for remediation
- Attach actual architecture diagrams and data flow diagrams

**🌐 Consumer Tool Restrictions:**
- Use generic system identifiers
- Reference architecture patterns without specific resource IDs
- Provide code examples conceptually without actual codebase exposure
- Reference compliance categories without specific requirement numbers
- Use role titles only for ownership
- Provide budget ranges rather than specific amounts
- Use relative timelines (weeks, months) without exact dates
- Abstract diagrams to generic patterns

**Verification Checklist:**
- [ ] All findings are technically accurate and reproducible
- [ ] Risk scores are calculated consistently using defined methodology
- [ ] Recommendations are specific and actionable (not generic "improve security")
- [ ] Effort and cost estimates are realistic based on organizational context
- [ ] Compliance gaps reference specific regulatory requirements
- [ ] Attack paths are realistic for identified threat actors
- [ ] Remediation roadmap is feasible given stated constraints
- [ ] Executive summary accurately reflects detailed findings
- [ ] Go/No-Go recommendation is justified and defensible

**Iteration Guidance:**
- If findings seem too numerous: Prioritize top risks, defer lower-priority items to next review
- If recommendations not actionable: Add more implementation details and examples
- If effort estimates questioned: Break down into sub-tasks with granular estimates
- If business pushback on critical findings: Provide attack path demonstrations showing exploit impact
- After remediation: Conduct follow-up review to validate fixes and update risk register
- If architecture changes: Update threat model and re-assess risk landscape

---
