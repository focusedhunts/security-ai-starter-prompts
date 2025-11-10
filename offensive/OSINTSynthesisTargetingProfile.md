# OSINT Synthesis and Target Profiling

**When to use this:** You're beginning an authorized red team engagement or penetration test and need to systematically gather and synthesize open-source intelligence about your target organization to identify potential attack vectors and build an operational profile.

**Why this is a separate prompt:** OSINT synthesis should happen BEFORE active testing or attack path planning. This prompt helps you organize reconnaissance findings into actionable intelligence without prematurely jumping into exploitation planning. It's a foundation-building task that informs all subsequent operational decisions.

**Four Principles Application:**
- **Context:** You provide engagement authorization, organizational scope, and collection objectives
- **Specificity:** You specify exact intelligence categories needed based on engagement goals
- **Structure:** The prompt uses four phases to build from raw data to synthesized profile
- **Iteration:** Start with basic profiling, iterate as you collect more intelligence, refine understanding progressively

---

## ⚠️ AUTHORIZATION CHECKPOINT

Before beginning OSINT collection, confirm you have:
- [ ] Written authorization for this specific organization
- [ ] Clear scope definition (what information gathering is permitted)
- [ ] Understanding of legal boundaries (public sources only, no unauthorized access)
- [ ] Client contact for scope questions about borderline sources
- [ ] Documented rules of engagement

**CRITICAL:** Even passive reconnaissance must be authorized. Collection from public sources is legal, but doing so for unauthorized security testing is not.

If ANY box is unchecked, STOP and obtain proper authorization.

---

## Part 1: OSINT Collection Strategy (Preparatory Guidance)

Use this section to plan your intelligence collection BEFORE using the synthesis prompt. This helps you understand what data to gather and from which sources.

### Understanding Your Collection Objectives

Before collecting OSINT, clarify what you need based on engagement goals:

**For External Penetration Tests:**
- Employee information (names, titles, email patterns)
- External infrastructure (domains, IPs, cloud services)
- Technology stack (web servers, frameworks, third-party services)
- Public-facing applications and services
- Business relationships and partnerships

**For Social Engineering Assessments:**
- Organizational structure and reporting relationships
- Employee communication patterns and language
- Company culture and values (for pretext development)
- Executive information and public profiles
- Trusted third-party relationships

**For Red Team Operations:**
- All of the above, plus:
- Physical locations and facility information
- Acquisition/merger history
- Technology refresh cycles
- Vendor relationships
- Public security posture statements

**For Bug Bounty Programs:**
- In-scope assets only (per program rules)
- Technology stack for in-scope applications
- Known security researchers working on program
- Historical vulnerability disclosures
- Development/security team information (for communication)

---

### OSINT Collection Framework

Below is a systematic framework for what to collect and where to find it. This is NOT an exhaustive list but represents high-value intelligence sources.

#### Category 1: Organizational Structure

**What to Collect:**
- Employee names and titles
- Department structures
- Reporting relationships
- Organizational hierarchy
- Office locations and facilities

**Where to Collect:**
- LinkedIn (company page, employee profiles, job titles)
- Company website (About Us, Team pages, Press Releases)
- SEC filings (if public company - executive compensation, organizational charts)
- Professional conference speaker lists
- Industry publications and interviews
- Social media profiles (Twitter/X, Facebook company pages)

**Tools to Use:**
- LinkedIn manual browsing (free) or LinkedIn Sales Navigator (paid)
- theHarvester (email/employee enumeration)
- hunter.io (email pattern identification)
- Companies House / SEC EDGAR (corporate filings)
- Google dorks: `site:linkedin.com/in "[Company Name]"`

**Data to Document:**
- Employee names (especially IT/Security roles)
- Email address patterns (firstname.lastname@company.com)
- Organizational chart (if reconstructable)
- Key decision-makers and their titles
- Security team composition and size

---

#### Category 2: Technology Stack and Infrastructure

**What to Collect:**
- Domain names and subdomains
- IP address ranges and ASNs
- Web technologies and frameworks
- Cloud service providers
- Email security (SPF, DMARC, DKIM records)
- Certificate transparency logs
- Third-party services and integrations

**Where to Collect:**
- DNS records (MX, TXT, A, AAAA records)
- Certificate Transparency logs
- Shodan / Censys (internet-wide scanning data)
- Job postings (technology requirements reveal stack)
- Developer profiles (GitHub, Stack Overflow)
- Error messages from public-facing applications
- HTTP headers and HTML source code
- Company tech blog posts

**Tools to Use:**
- Subdomain enumeration: Amass, Subfinder, Assetfinder
- DNS reconnaissance: dig, nslookup, DNSdumpster
- Technology identification: Wappalyzer, BuiltWith, WhatWeb
- Certificate transparency: crt.sh, Censys
- Cloud detection: CloudEnum, cloud_enum
- Port/service scanning: Shodan, Censys (not direct scanning - use existing data)
- ASN lookup: Hurricane Electric BGP Toolkit

**Data to Document:**
- All discovered domains and subdomains
- IP ranges owned by organization
- Cloud services in use (AWS, Azure, GCP)
- Web frameworks and CMS platforms
- Programming languages and versions (from job posts)
- Email security posture
- External services and APIs
- SSL/TLS certificate patterns

---

#### Category 3: Digital Footprint and Public Presence

**What to Collect:**
- Social media accounts (corporate and key employees)
- Public code repositories
- Public documents (PDFs, presentations, spreadsheets)
- News articles and press coverage
- Breach/leak exposure
- Domain registration history
- Archived website versions

**Where to Collect:**
- GitHub / GitLab (public repositories, contribution history)
- Document metadata (Google dorks for PDFs, DOCX, XLSX)
- Have I Been Pwned (breach exposure)
- dehashed.com (credential leaks - for pattern analysis only)
- Wayback Machine / Archive.org (historical snapshots)
- Social media platforms (Twitter/X, Facebook, Instagram)
- YouTube (company channels, employee presentations)
- SlideShare / Scribd (presentations)
- Patents and trademark databases

**Tools to Use:**
- Git reconnaissance: GitDorker, TruffleHog, GitLeaks
- Metadata extraction: FOCA, ExifTool, metagoofil
- Google dorks: `site:target.com filetype:pdf`
- Wayback Machine for historical data
- Social media scrapers (within ToS): Social-Analyzer
- Breach data: Have I Been Pwned API

**Data to Document:**
- Exposed repositories and code samples
- Leaked credentials (for pattern analysis - never use unauthorized)
- Document metadata (authors, software versions, internal paths)
- Historical infrastructure changes
- Security incidents mentioned in news
- Employee technical skill sets from profiles
- Conference presentations and technical talks

---

#### Category 4: Business Intelligence and Relationships

**What to Collect:**
- Partnership and vendor relationships
- Acquisition and merger history
- Technology vendors and service providers
- Supply chain connections
- Industry affiliations
- Regulatory/compliance requirements

**Where to Collect:**
- Company website (Partners page, Case Studies)
- Press releases and news articles
- SEC filings (Material Agreements section)
- Industry conference sponsor lists
- Technology vendor case studies
- LinkedIn company connections
- Job postings (integration requirements)

**Tools to Use:**
- Google News search
- Crunchbase (company relationships, funding)
- SEC EDGAR (public companies)
- LinkedIn company page analysis
- Industry-specific databases

**Data to Document:**
- Key technology vendors
- Managed service providers
- Cloud/hosting providers
- Third-party authentication services
- Supply chain partners
- Industry regulatory requirements (HIPAA, PCI-DSS, etc.)

---

### Collection Best Practices

**Legal and Ethical Boundaries:**
- Only collect from public sources
- Do not create fake accounts to access restricted information
- Do not use social engineering during OSINT collection (unless specifically authorized)
- Respect website Terms of Service
- Do not perform active scanning (use existing Shodan/Censys data)
- Document your sources for evidence purposes

**Operational Security:**
- Use VPN or proxy for collection (don't reveal your real IP to target)
- Avoid logging into personal accounts while researching target
- Use separate browser profiles or VMs for OSINT work
- Be aware that some collection activities may be logged by target
- Don't over-query a single source (rate limiting, suspicion)

**Documentation During Collection:**
- Note the source URL for every piece of information
- Take screenshots for evidence
- Record collection timestamps
- Document tools and commands used
- Maintain chain of custody for findings

---

### Collection Checklist

Before proceeding to synthesis, ensure you have collected:

**Organizational:**
- [ ] 20+ employee names with titles
- [ ] Email address pattern confirmed
- [ ] Key decision-maker identification
- [ ] Department structure understanding

**Technical:**
- [ ] Complete subdomain list
- [ ] Technology stack identification
- [ ] Cloud service provider confirmation
- [ ] Third-party service inventory

**Digital Footprint:**
- [ ] Social media profiles catalogued
- [ ] Public code repositories reviewed
- [ ] Historical website snapshots examined
- [ ] Breach exposure checked

**Business Context:**
- [ ] Key vendor relationships identified
- [ ] Industry compliance requirements understood
- [ ] Recent news/changes documented

---

## Part 2: OSINT Synthesis Prompt (Multi-Phase)

Now that you've collected raw intelligence, use this multi-phase prompt to synthesize findings into an actionable target profile.

**How to use this prompt:**
1. Copy the entire prompt below
2. Fill in your engagement context and authorization details
3. Paste your collected OSINT data into each phase section
4. Work through phases sequentially (AI will build understanding progressively)
5. Review synthesis output and iterate if needed

---

### STARTER PROMPT TEMPLATE

```markdown
I am conducting an authorized security assessment and need to synthesize open-source intelligence I've collected about the target organization into an actionable operational profile. I will provide data in four phases, and I need you to help me organize, analyze, and prioritize this intelligence.

ENGAGEMENT AUTHORIZATION:
Client: [CLIENT_NAME]
🏢 Enterprise: "TechCorp Industries - Contract #RT-2024-089"
🌐 Consumer: "Authorized target organization under contract"

Engagement Type: [TYPE]
Examples: "External penetration test", "Red team operation", "Social engineering assessment", "Bug bounty program"

Authorization Scope: [WHAT'S AUTHORIZED]
🏢 Enterprise: "All TechCorp external assets, including subsidiaries. Authorized: passive reconnaissance, active scanning of external IPs, social engineering of employees. Prohibited: physical security testing, DoS attacks."
🌐 Consumer: "External assessment of authorized target. Passive reconnaissance and active testing permitted per contract."

Engagement Timeline: [DATES]
Example: "December 1-15, 2024"

Primary Objectives: [ENGAGEMENT GOALS]
Examples:
- "Gain initial access to corporate network"
- "Demonstrate social engineering effectiveness"
- "Identify external vulnerabilities in customer-facing applications"
- "Test detection and response capabilities"

IMPORTANT CONTEXT INSTRUCTIONS:

You are a red team operator assistant helping synthesize reconnaissance data. Your role is to:
- Organize raw OSINT into structured intelligence
- Identify patterns and relationships in the data
- Highlight high-value targets and attack vectors
- Prioritize findings based on engagement objectives
- Provide tactical recommendations for next steps

You must NOT:
- Suggest collection methods that violate authorization
- Recommend testing outside stated scope
- Make assumptions about data I haven't provided
- Suggest social engineering pretexts unless engagement authorizes them
- Provide generic advice disconnected from my specific findings

Let's work through this systematically in four phases.

---

PHASE 1: ORGANIZATIONAL STRUCTURE MAPPING

In this phase, I'm providing employee and organizational data I've collected. Help me map the organizational structure, identify high-value targets, and understand communication patterns.

EMPLOYEE INTELLIGENCE COLLECTED:

Employee List (format: Name | Title | Department | Source):
🏢 Enterprise:
- John Smith | Chief Technology Officer | Executive | LinkedIn
- Sarah Johnson | VP of Engineering | Engineering | Company website
- Mike Chen | Security Director | InfoSec | LinkedIn
- [Continue with your collected employees...]

🌐 Consumer:
- [Employee A] | Executive Role | Executive | [Source]
- [Employee B] | Engineering Leadership | Engineering | [Source]
- [Employee C] | Security Role | Security Team | [Source]
- [Continue with genericized names...]

Email Address Pattern:
🏢 Enterprise: "firstname.lastname@techcorp.com (confirmed from multiple sources)"
🌐 Consumer: "Standard corporate email pattern observed"

Organizational Observations:
[Note any patterns you observed during collection]
Example:
- Large engineering team (50+ employees on LinkedIn with engineering titles)
- Small security team (only 3-4 dedicated security roles identified)
- Recent hiring surge in cloud engineering (10+ job posts in past 3 months)
- Executive team very active on social media (frequent posts about company)

Departmental Structure (if identifiable):
- Executive Team: [Size/composition]
- Engineering: [Size/composition]
- IT/Infrastructure: [Size/composition]
- Security: [Size/composition]
- [Other relevant departments]

Key Individuals of Interest:
[Who might be high-value targets and why?]
🏢 Enterprise:
- Mike Chen (Security Director): Highly visible on LinkedIn, posts about security tools in use
- Sarah Johnson (VP Engineering): Has GitHub account with public contributions, reveals tech stack

🌐 Consumer:
- [Individual 1] (Security Role): Public profile reveals security tool preferences
- [Individual 2] (Engineering Leadership): Technical background suggests access to critical systems

PHASE 1 TASK:

Based on this organizational intelligence:

1. **Map the organizational structure** - How is this organization structured? Who reports to whom (if determinable)?

2. **Identify high-value targets** - Which individuals would be most valuable for:
   - Initial access (who has external access, VPN, cloud resources?)
   - Privilege escalation (who has elevated permissions?)
   - Persistence (who manages critical infrastructure?)
   - Social engineering (who is most visible/accessible?)

3. **Communication patterns** - What does the email pattern tell us? Are there predictable patterns we can leverage?

4. **Security team analysis** - How mature is their security program based on team size and roles? What does this suggest about detection capabilities?

5. **Organizational culture insights** - What does employee social media activity suggest about company culture, security awareness, or exploitable patterns?

Provide your analysis in structured format:

**Organizational Structure:**
[Your mapping of departments and relationships]

**High-Value Targets:**
[Priority list with rationale for each]

**Communication Patterns:**
[Email patterns and other observable communication methods]

**Security Posture Assessment:**
[What organizational structure reveals about security maturity]

**Cultural Observations:**
[Relevant cultural factors that might affect operational approach]

---

[Wait for Phase 1 response before proceeding to Phase 2]

---

PHASE 2: TECHNOLOGY STACK AND INFRASTRUCTURE ANALYSIS

Now I'm providing technical intelligence about their infrastructure and technology stack. Help me understand their technical environment, identify potential vulnerabilities, and map attack surface.

INFRASTRUCTURE INTELLIGENCE:

Domains and Subdomains Discovered:
🏢 Enterprise:
- techcorp.com (primary domain)
- mail.techcorp.com (email server)
- vpn.techcorp.com (remote access)
- api.techcorp.com (API gateway)
- [Continue with your discoveries...]

🌐 Consumer:
- [primary-domain] (main website)
- [subdomain-1] (mail service)
- [subdomain-2] (remote access)
- [subdomain-3] (API endpoint)
- [Continue with findings...]

IP Address Ranges (if identified):
🏢 Enterprise: "203.0.113.0/24, ASN: AS64496 - TechCorp Networks"
🌐 Consumer: "[IP range], [ASN information]"

Cloud Infrastructure Detected:
🏢 Enterprise:
- AWS (S3 buckets identified via cert transparency: s3.amazonaws.com/techcorp-backups)
- Azure (mail services: outlook.office365.com)
- Cloudflare (CDN and DDoS protection observed)

🌐 Consumer:
- [Cloud Provider 1] (specific services if identifiable)
- [Cloud Provider 2] (services detected)
- [CDN or security services]

Technology Stack Identified:

Web Technologies:
🏢 Enterprise:
- Web server: nginx 1.21.0
- Framework: React (detected from job postings and JavaScript files)
- Programming language: Node.js (from job requirements)
- Database: PostgreSQL (mentioned in engineer's conference talk)

🌐 Consumer:
- Web server: [Detected technology]
- Framework: [If identified]
- Programming language: [If known]
- Database: [If identifiable]

Third-Party Services:
🏢 Enterprise:
- Auth0 (authentication - from JavaScript includes)
- SendGrid (email service - from headers)
- Stripe (payments - from job posting requirements)
- GitHub (code hosting - from employee profiles)

🌐 Consumer:
- [Authentication service]
- [Email service]
- [Payment processor]
- [Development platforms]

Email Security Posture:
🏢 Enterprise:
SPF Record: v=spf1 include:spf.protection.outlook.com ~all
DMARC: v=DMARC1; p=none; (DMARC policy is permissive, not enforced)
🌐 Consumer:
- SPF: [Your findings]
- DMARC: [Policy identified]

SSL/TLS Certificates Observations:
- Certificate Authority: [Issuer]
- Wildcard certificates: [Yes/No - if yes, note subdomains]
- Certificate transparency findings: [Internal subdomains revealed]

Public-Facing Applications:
🏢 Enterprise:
- Corporate website (https://techcorp.com) - Marketing site
- Customer portal (https://portal.techcorp.com) - Login required
- API documentation (https://api.techcorp.com/docs) - Public access
- Career site (https://careers.techcorp.com) - Public access

🌐 Consumer:
- [Application 1 and purpose]
- [Application 2 and purpose]
- [Application 3 and purpose]

Infrastructure Observations:
[Note anything unusual or interesting]
Example:
- VPN subdomain suggests remote workforce or remote access for employees
- Multiple API subdomains suggest microservices architecture
- Staging/dev subdomains exposed (staging.techcorp.com returned 200)
- Old/legacy subdomains still responding (old.techcorp.com)

PHASE 2 TASK:

Based on this technical intelligence:

1. **Infrastructure mapping** - Provide a structured map of their external infrastructure (domains, IPs, cloud services)

2. **Technology stack analysis** - What does their tech stack reveal about:
   - Potential vulnerabilities (known framework issues, outdated versions)
   - Attack surface (exposed services, API endpoints)
   - Defensive capabilities (security services in use)

3. **Attack surface prioritization** - Which assets are most interesting for:
   - Initial access attempts
   - Credential harvesting
   - Data exposure
   - Service exploitation

4. **Email security assessment** - What does their SPF/DMARC configuration suggest about email spoofing potential?

5. **Third-party service risks** - Which third-party services might be leveraged for:
   - OAuth/authentication bypass
   - Supply chain attacks
   - Trusted relationship exploitation

6. **Misconfiguration identification** - Based on what I've found, what misconfigurations or exposures warrant investigation?

Provide analysis in structured format:

**Infrastructure Map:**
[Organized view of their external presence]

**Technology Stack Summary:**
[Key technologies with security implications]

**Prioritized Attack Surface:**
[Ranked list of interesting targets with rationale]

**Email Security Analysis:**
[Spoofing potential and email-based attack viability]

**Third-Party Risk Assessment:**
[Services that might be exploitable]

**Notable Misconfigurations:**
[Findings that suggest immediate investigation opportunities]

---

[Wait for Phase 2 response before proceeding to Phase 3]

---

PHASE 3: DIGITAL FOOTPRINT AND EXPOSURE ANALYSIS

I'm providing data about their digital footprint - code repositories, documents, breaches, and historical data. Help me identify information leakage, exposed secrets, and exploitable patterns.

CODE REPOSITORY INTELLIGENCE:

Public Repositories Found:
🏢 Enterprise:
Repository: github.com/techcorp/public-api-docs
- Purpose: API documentation for customers
- Last updated: 3 months ago
- Notable findings: Includes example API keys (marked as examples, but pattern is revealing)

Repository: github.com/jsmith-techcorp/personal-scripts
- Owner: John Smith (CTO personal account)
- Purpose: Utility scripts
- Notable findings: Contains connection scripts with internal IP address patterns

🌐 Consumer:
Repository: [Repository 1]
- Purpose: [What it contains]
- Notable findings: [What's interesting or concerning]

Repository: [Repository 2]
- Owner: [If notable]
- Notable findings: [Security relevant information]

Code Analysis:
[Patterns observed in public code]
Example:
- Coding standards reveal internal API naming conventions
- Error handling patterns suggest internal architecture
- Dependencies show technology stack details
- Comments contain internal system names

DOCUMENT INTELLIGENCE:

Public Documents Found (PDFs, presentations, etc.):
🏢 Enterprise:

Document: "TechCorp Infrastructure Overview 2023.pdf"
- Source: Found via Google dork: site:techcorp.com filetype:pdf
- Content summary: Architecture presentation for partners
- Notable findings:
  * Network diagram showing internal subnets (10.0.0.0/8)
  * VPN solution mentioned (Cisco AnyConnect)
  * Internal project codenames revealed

Document: "Security Policies - TechCorp.docx"
- Source: Exposed on staging.techcorp.com
- Metadata: Author "Mike Chen", created with Microsoft Office 2019
- Notable findings:
  * Password policy requirements (min 10 chars, complexity rules)
  * MFA is "recommended" not required for standard users
  * Security software mentioned (CrowdStrike EDR)

🌐 Consumer:
Document: [Document 1]
- Source: [Where found]
- Notable findings: [Security relevant information]

Metadata Extracted:
[Document metadata revealing internal information]
Example:
- Internal usernames in document authors
- Software versions (Office 2019, Adobe Acrobat DC)
- Internal network paths (C:\Users\jsmith\Documents\...)
- Template locations revealing internal file structure

BREACH AND LEAK EXPOSURE:

Breach Database Findings:
🏢 Enterprise:
- Have I Been Pwned: 47 techcorp.com emails in Collection #1 breach (2019)
- Password patterns observed: [generic patterns only - never actual passwords]
- Notable accounts: mike.chen@techcorp.com, sarah.johnson@techcorp.com

🌐 Consumer:
- [Number] corporate emails found in historical breaches
- Account patterns: [Observed patterns, never specific passwords]
- High-value accounts exposed: [Roles, not names if using consumer AI]

Analysis Notes:
[What breach data reveals about security practices]
Example:
- Password reuse appears common (similar patterns across breaches)
- No evidence of password rotation after breaches
- Corporate credentials used on external services

HISTORICAL INTELLIGENCE:

Wayback Machine Findings:
🏢 Enterprise:
- 2020 snapshot shows different infrastructure (on-premise hosting)
- 2022 snapshot shows migration to cloud (AWS references appear)
- Employee login portal was publicly accessible in 2019 (now requires VPN)

🌐 Consumer:
- Historical snapshots show [evolution of infrastructure]
- Previous configurations: [Notable changes over time]

Technology Evolution:
[How their stack has changed over time]
Example:
- Migrated from on-premise to cloud (2022)
- Changed authentication providers (Auth0 adopted in 2023)
- Old domains still responding (legacy.techcorp.com from pre-2020)

SOCIAL MEDIA AND ONLINE PRESENCE:

Employee Social Media Activity:
🏢 Enterprise:
- John Smith (CTO): Very active on LinkedIn, posts about AWS architecture decisions
- Mike Chen (Security Director): Twitter account shares conference talks, mentions tools in use
- Sarah Johnson (VP Eng): GitHub contributions show technology preferences

🌐 Consumer:
- [Role 1]: Active on [platform], shares [type of information]
- [Role 2]: Public profile reveals [operational details]

Company Social Media:
- Official accounts: [LinkedIn, Twitter, Facebook presence]
- Content themes: [What they promote publicly]
- Security-relevant posts: [Any security program mentions, achievements, tools]

PHASE 3 TASK:

Based on this digital footprint and exposure data:

1. **Information leakage assessment** - What sensitive information has been inadvertently exposed through:
   - Public code repositories
   - Document metadata
   - Historical snapshots
   - Social media activity

2. **Credential exposure analysis** - What do breach databases reveal about:
   - Password patterns and policies
   - Account security practices
   - High-value accounts at risk

3. **Technical intelligence extraction** - What specific technical details can be leveraged for:
   - Crafting convincing social engineering pretexts
   - Understanding internal architecture
   - Identifying authentication mechanisms
   - Mapping internal networks (from documents/code)

4. **Historical evolution insights** - What does infrastructure evolution suggest about:
   - Legacy systems that might still exist
   - Migration-related misconfigurations
   - Forgotten or unmonitored assets

5. **OPSEC opportunities** - Based on employee social media activity, what operational security opportunities exist for:
   - Social engineering pretext development
   - Identifying less security-aware targets
   - Understanding company culture for believable pretexts

Provide analysis in structured format:

**Information Leakage Summary:**
[Critical exposures organized by source]

**Credential Intelligence:**
[What breach data reveals - patterns only, never specific passwords]

**Technical Intelligence Highlights:**
[Actionable technical details from documents/code/history]

**Infrastructure Evolution:**
[How changes might create opportunities]

**OPSEC Exploitation Opportunities:**
[How to leverage social media and public presence]

---

[Wait for Phase 3 response before proceeding to Phase 4]

---

PHASE 4: BUSINESS CONTEXT AND RELATIONSHIP MAPPING

Finally, I'm providing business intelligence about their partnerships, vendors, and industry context. Help me identify supply chain risks, trusted relationships, and business-driven attack vectors.

PARTNERSHIP AND VENDOR INTELLIGENCE:

Technology Vendors Identified:
🏢 Enterprise:
- AWS (cloud infrastructure provider)
- Auth0 (authentication service)
- CrowdStrike (endpoint security)
- Cisco (VPN infrastructure)
- SendGrid (email service)
- Stripe (payment processing)

🌐 Consumer:
- [Cloud provider]
- [Authentication service]
- [Security vendors]
- [Infrastructure providers]

Managed Service Providers:
🏢 Enterprise:
- "CloudOps Partners" (AWS management - from case study on their website)
- "SecureIT Solutions" (SOC monitoring - from job posting mentioning them)

🌐 Consumer:
- [MSP 1] with [service type]
- [MSP 2] with [service type]

Business Partnerships:
🏢 Enterprise:
- Strategic partnership with "HealthCare Partners Network" (from press release)
- Integration with "DataAnalytics Co" (from API documentation)
- Reseller relationship with "Enterprise Solutions Inc"

🌐 Consumer:
- Partnership with [Organization 1]
- Integration with [Organization 2]

Third-Party Access Points:
[Based on job postings, documentation, partnerships]
Example:
- Vendors have VPN access for support (from security policy document)
- MSP has access to "monitoring and management tools" (from case study)
- Partners can access API with special authentication (from API docs)

BUSINESS INTELLIGENCE:

Company Background:
🏢 Enterprise:
- Founded: 2015
- Industry: Healthcare Technology
- Size: ~200 employees (from LinkedIn)
- Revenue: $50M (from Crunchbase)
- Funding: Series B, $25M (2023)

🌐 Consumer:
- Industry: [Sector]
- Approximate size: [Employee count range]
- Maturity: [Startup/Growth/Established]

Recent News and Changes:
[Significant events that might affect security]
🏢 Enterprise:
- October 2024: Announced acquisition of "MedTech Startup" (from press release)
- September 2024: Data breach mentioned in industry news (compromised partner vendor)
- August 2024: Leadership change - new CISO hired (from LinkedIn)

🌐 Consumer:
- Recent events: [Organizational changes, incidents, announcements]

Regulatory Environment:
🏢 Enterprise:
- Industry regulations: HIPAA (healthcare data)
- Compliance requirements: SOC 2 Type II (mentioned in sales materials)
- Data residency: US-only (from privacy policy)

🌐 Consumer:
- Regulatory requirements: [Industry-specific regulations]
- Compliance frameworks: [Known compliance standards]

Acquisition/Merger History:
- [List any acquisitions that might mean integrated/legacy systems]
- [Note any subsidiaries or related companies]

PHASE 4 TASK:

Based on this business context and relationship intelligence:

1. **Supply chain risk analysis** - Which vendors, partners, or MSPs represent potential:
   - Initial access vectors (trusted relationships)
   - Privilege escalation paths (vendor with elevated access)
   - Lateral movement opportunities (interconnected systems)

2. **Trust relationship mapping** - Create a map of trust relationships showing:
   - Which organizations have technical access to target systems
   - What level of access each relationship provides
   - How trust could be exploited within engagement scope

3. **Business context implications** - How do business factors affect operational approach:
   - Recent acquisitions (integrated systems, diverse security postures)
   - Industry regulations (security tool predictions, compliance-driven controls)
   - Company maturity (security program sophistication)
   - Recent incidents (current security focus, defensive improvements)

4. **Regulatory constraints** - What compliance requirements suggest about:
   - Mandatory security controls likely in place
   - Audit and monitoring requirements
   - Data handling and retention
   - Incident response capabilities

5. **Third-party attack vectors** - Specific recommendations for:
   - Which third-party relationships are most exploitable
   - How to leverage trusted status for initial access
   - What pretexts would be most believable (vendor support, partner integration)

Provide analysis in structured format:

**Supply Chain Risk Map:**
[Vendors/partners with their access levels and exploit potential]

**Trust Relationship Diagram:**
[Visual or structured representation of who trusts whom]

**Business Context Security Implications:**
[How business factors shape security posture]

**Regulatory Control Predictions:**
[Likely security controls based on compliance requirements]

**Third-Party Exploitation Strategy:**
[Prioritized list of third-party vectors with operational approaches]

---

[Wait for Phase 4 response before proceeding to final synthesis]

---

FINAL SYNTHESIS REQUEST:

Now that we've worked through all four phases, I need you to synthesize everything into a comprehensive target profile that will guide my operational planning.

Create two outputs:

**OUTPUT 1: EXECUTIVE SUMMARY (High-Level Narrative)**

Provide a 3-4 paragraph executive summary that:
- Describes the target organization's security posture based on all collected intelligence
- Identifies the TOP 3-5 most promising attack vectors for this engagement
- Highlights critical findings that should drive operational focus
- Assesses likely detection/response capabilities based on observed maturity

Write this as if briefing a red team lead before operations begin.

**OUTPUT 2: STRUCTURED OPERATIONAL PROFILE (Detailed Intelligence)**

Organize all findings into a structured format suitable for operational reference:

1. **Target Overview**
   - Organization size, structure, and industry
   - Security team composition and maturity indicators
   - Recent changes or incidents affecting security posture

2. **Priority Attack Vectors** (ranked by feasibility + impact)
   - Attack Vector 1: [Name]
     - Description: [What this vector is]
     - Entry Point: [How to exploit]
     - Requirements: [What's needed]
     - Detection Risk: [Likelihood of being caught]
     - Value: [What this achieves]
   
   [Continue for each priority vector]

3. **High-Value Targets** (individuals)
   - Target 1: [Name/Role]
     - Access Level: [What they can access]
     - Security Posture: [Awareness indicators]
     - Contact Methods: [Email, phone, social media]
     - Pretext Opportunities: [How to approach]
   
   [Continue for each HVT]

4. **Technical Intelligence Summary**
   - External infrastructure map
   - Technology stack with versions
   - Identified misconfigurations
   - Third-party services and integrations

5. **Information Exposures**
   - Credentials in breaches (pattern analysis only)
   - Leaked technical documents
   - Sensitive code repositories
   - Metadata intelligence

6. **Trust Relationships and Supply Chain**
   - Key vendors with access
   - Partnership integrations
   - MSP/third-party services
   - Exploitation opportunities

7. **Defensive Capability Assessment**
   - Known security tools
   - Monitoring/detection maturity
   - Incident response readiness
   - Security team size and expertise

8. **Recommended Next Steps**
   - Immediate operational priorities
   - Additional intelligence gaps to fill
   - Suggested initial approach
   - Red flags or cautions

FORMAT THIS OUTPUT AS STRUCTURED DATA - use tables, bullet hierarchies, or clear sections that can be referenced quickly during operations.

---

**CONSTRAINTS FOR ALL PHASES:**

Throughout this synthesis, you must:

✅ DO:
- Organize and analyze the intelligence I provided
- Identify patterns and relationships in the data
- Prioritize findings based on my engagement objectives
- Highlight gaps where additional intelligence would be valuable
- Provide tactical recommendations grounded in my specific findings
- Assess realistic attack vectors based on actual discovered infrastructure
- Consider operational security implications of each approach

❌ DO NOT:
- Suggest collection methods beyond what I've already done
- Recommend testing or exploitation (this is intelligence synthesis only)
- Make assumptions about systems or data I haven't provided
- Suggest social engineering pretexts unless my engagement explicitly authorizes them
- Provide generic penetration testing advice disconnected from my findings
- Recommend actions outside my stated authorization scope
- Exaggerate findings or create "threats" not supported by evidence

**YOUR ROLE:** You are helping me organize and analyze intelligence to inform operational planning. You are NOT planning the actual operation or suggesting how to exploit findings. That comes later, after I've validated this intelligence and received additional approvals.

Begin with Phase 1 analysis.
```

---

## Using This Multi-Phase Prompt

### Workflow Overview

1. **Complete OSINT collection** using Part 1 guidance (do this BEFORE using the synthesis prompt)
2. **Copy the entire prompt template** from Part 2
3. **Fill in authorization and context** sections with your engagement details
4. **Paste Phase 1 data** (organizational intelligence you collected)
5. **Submit to AI** and review Phase 1 synthesis
6. **Continue to Phase 2** by pasting technical intelligence
7. **Review Phase 2 synthesis**, identify any collection gaps
8. **Proceed through Phases 3 and 4** similarly
9. **Request final synthesis** once all phases complete
10. **Validate AI synthesis** against your raw intelligence (AI should organize, not invent)

### Why Multi-Phase Structure Works

**Prevents Context Overload:**
- Submitting all OSINT at once overwhelms both you and the AI
- Phased approach builds understanding progressively
- Each phase focuses AI attention on specific intelligence categories

**Enables Validation Checkpoints:**
- Review Phase 1 synthesis before moving to Phase 2
- Catch misinterpretations early before they propagate
- Identify missing intelligence while collection is still feasible

**Mirrors Operational Workflow:**
- Intelligence collection happens incrementally in real engagements
- You can use early phases even if later intelligence is still being gathered
- Natural progression from organizational → technical → historical → business

**Improves Synthesis Quality:**
- AI builds contextual understanding across phases
- Connections between phases become clearer (organizational structure + technology stack = specific attack vectors)
- Final synthesis is more coherent because AI has full picture

---

## Iteration and Refinement

### If Phase Synthesis Is Too Generic

**Problem:** AI provides textbook answers not grounded in your specific findings.

**Solution - Follow-up prompt:**
```markdown
Your Phase [X] analysis was too generic. I need you to focus specifically on [SPECIFIC ASPECT] from my data.

For example, you said "[GENERIC STATEMENT AI MADE]" but I need specific analysis of [YOUR SPECIFIC FINDING].

Re-analyze Phase [X] with focus on:
- [Specific element 1 from your data]
- [Specific element 2 from your data]
- [Specific element 3 from your data]

Ground your analysis in the ACTUAL data I provided, not general penetration testing advice.
```

### If You Discover More Intelligence Mid-Process

**Problem:** You collected additional OSINT after completing a phase.

**Solution - Addendum prompt:**
```markdown
I've collected additional intelligence for Phase [X]. Please update your Phase [X] analysis with this new data:

[Paste new findings]

Specifically, how does this new information:
1. Change your assessment of [previous finding]?
2. Create new opportunities for [attack vector]?
3. Affect your prioritization of [target/asset]?

Provide an updated Phase [X] analysis incorporating this new intelligence.
```

### If AI Makes Assumptions Beyond Your Data

**Problem:** AI suggests infrastructure or capabilities you didn't mention.

**Solution - Correction prompt:**
```markdown
You suggested [ASSUMED ELEMENT] but I did not provide information about this. Please base your analysis ONLY on intelligence I explicitly provided.

Remove assumptions about:
- [Assumption 1]
- [Assumption 2]

Re-analyze with constraint: "You must only use information from the data I provided. If I didn't mention something, note it as an intelligence gap rather than assuming it exists."
```

### If You Need Deeper Analysis of One Area

**Problem:** One finding needs more detailed examination than phase synthesis provided.

**Solution - Focused deep-dive prompt:**
```markdown
From Phase [X] synthesis, you identified [SPECIFIC FINDING] as significant. I need a detailed deep-dive analysis of just this finding.

Finding: [Restate the finding]

Provide detailed analysis covering:
1. Exploitation potential - How specifically could this be leveraged within my authorization?
2. Detection risk - What defensive visibility exists for this approach?
3. Requirements - What do I need (access, tools, time) to exploit this?
4. Alternatives - If this approach fails, what alternatives exist?
5. Chain potential - How does this enable further access or movement?

Focus exclusively on this single finding with maximum depth.
```

---

## Verification Checklist

Before using synthesized intelligence for operational planning:

### Intelligence Validation

- [ ] **Source verification** - All intelligence is from authorized public sources
- [ ] **Data accuracy** - Spot-check AI synthesis against raw data (AI should organize, not fabricate)
- [ ] **Relationship accuracy** - Verify AI correctly connected related findings
- [ ] **Priority validation** - AI's prioritization aligns with engagement objectives
- [ ] **Gap identification** - AI correctly identified missing intelligence vs making assumptions

### Scope Compliance

- [ ] **Authorization boundaries** - All synthesized attack vectors are within scope
- [ ] **Prohibited actions avoided** - No recommendations violate rules of engagement
- [ ] **Third-party caution** - Recommendations involving third parties consider legal boundaries
- [ ] **Data handling** - Synthesis doesn't recommend unauthorized data access

### Operational Readiness

- [ ] **Actionability** - Synthesis provides specific, implementable intelligence (not generic advice)
- [ ] **Realistic assessment** - Defensive capability assessment is grounded in evidence, not speculation
- [ ] **Detection consideration** - Synthesis acknowledges operational security implications
- [ ] **Next steps clarity** - Clear understanding of what to do with this intelligence

### Documentation Quality

- [ ] **Evidence trail** - Can trace synthesized findings back to original sources
- [ ] **Professional presentation** - Synthesis is suitable for client briefing or team handoff
- [ ] **Sanitization** - If using consumer AI, verify no sensitive client data in prompts
- [ ] **Completeness** - Synthesis addresses all engagement objectives stated at beginning

---

## Common Mistakes to Avoid

### ❌ Mixing Collection and Synthesis

**Mistake:** Trying to use AI for both OSINT collection and synthesis simultaneously.

**Why It Fails:** AI cannot access real-time data, query APIs, or browse websites effectively. It can only work with data you provide.

**Correct Approach:** Use Part 1 to guide manual collection with tools, then use Part 2 to synthesize what you collected.

---

### ❌ Providing Unsanitized Data to Consumer AI

**Mistake:** Pasting actual client names, employee names, internal IPs into ChatGPT or other consumer services.

**Why It Fails:** This data may be retained, used for training, or exposed in breaches. Violates client confidentiality.

**Correct Approach:** 
- 🏢 Use enterprise AI with DPA for real client data
- 🌐 Sanitize everything when using consumer AI ("Target Organization", "Employee A", "[IP Range]")

---

### ❌ Accepting AI Synthesis Without Validation

**Mistake:** Taking AI's analysis as fact without cross-checking against raw intelligence.

**Why It Fails:** AI may misinterpret data, create false connections, or hallucinate facts not in your data.

**Correct Approach:** Treat synthesis as "draft analysis" that YOU must validate. Spot-check AI claims against your original sources.

---

### ❌ Over-Relying on AI for Prioritization

**Mistake:** Letting AI's priority rankings override your professional judgment about the engagement.

**Why It Fails:** AI doesn't understand your client's specific concerns, your team's capabilities, or nuanced engagement objectives.

**Correct Approach:** Use AI prioritization as input, but YOU make final decisions based on engagement context AI can't fully grasp.

---

### ❌ Using Synthesis for Direct Exploitation

**Mistake:** Taking synthesized intelligence directly into active exploitation without validation or additional planning.

**Why It Fails:** Synthesis is reconnaissance output, not exploitation planning. It identifies possibilities, not proven approaches.

**Correct Approach:** Synthesis informs NEXT phase of planning (attack path development, exploitation methodology), which requires separate prompts and validation.

---

### ❌ Skipping Phases or Combining Them

**Mistake:** Dumping all collected OSINT into one massive prompt instead of working through phases.

**Why It Fails:** Context overload reduces synthesis quality. AI loses focus. You can't validate incrementally.

**Correct Approach:** Work through phases sequentially even if you've collected all intelligence. This produces better analysis.

---

### ❌ Not Documenting Intelligence Sources

**Mistake:** Providing intelligence to AI without noting where each piece came from.

**Why It Fails:** Cannot validate AI synthesis without source traceability. Cannot reproduce findings. Professionalism suffers.

**Correct Approach:** In your data, include source for each item: "Email pattern observed from 10+ LinkedIn profiles and company website contact page"

---

## Next Steps After OSINT Synthesis

Once you have a complete target profile from this OSINT synthesis:

### Immediate Actions

1. **Validate key findings** - Cross-check high-priority findings against multiple sources
2. **Fill intelligence gaps** - Identify missing information needed for operational planning
3. **Brief the team** - Share synthesized profile with red team members
4. **Client sync** - Confirm any ambiguous scope questions before planning exploitation

### Subsequent Prompt Development

The synthesized target profile feeds into these operational phases:

**Attack Path Planning** (separate prompt):
- Use organizational structure + tech stack to map attack chains
- Leverage trust relationships for initial access vectors
- Plan multi-stage operations based on synthesized intelligence

**Social Engineering Development** (if authorized):
- Use cultural observations + employee intelligence for pretext creation
- Leverage business context for believable scenarios
- Target selection based on HVT analysis

**Technical Exploitation Planning**:
- Focus on prioritized attack surface from Phase 2
- Develop exploitation approaches for identified technologies
- Plan evasion based on defensive capability assessment

**Operational Security Planning**:
- Use security team analysis to predict detection
- Plan communication methods based on monitoring assessment
- Develop counter-surveillance for identified defensive tools

### This Intelligence Profile Is Living Document

As engagement progresses:
- Update profile with newly discovered information
- Re-run phases when significant new intelligence emerges
- Refine priorities based on early operation results
- Document what intelligence proved accurate vs inaccurate

---

## Storage and Handling

**Intelligence Security:**

🏢 **Enterprise AI** - If you used enterprise tools:
- Store sanitized synthesis in engagement documentation
- Original raw intelligence stays in secure client folder
- Synthesis can be shared with authorized team members

🌐 **Consumer AI** - If you used consumer services:
- Never store consumer AI prompts in client folders (they contain client data)
- Re-create synthesis in secure environment with real client details
- Original intelligence should never have been in consumer prompts in first place

**Retention:**
- Intelligence synthesis is client work product - follows client data retention policies
- After engagement, intelligence should be archived or destroyed per contract
- Lessons learned (techniques, not client details) can be retained for future work
