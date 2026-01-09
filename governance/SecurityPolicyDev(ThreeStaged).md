# Security Policy Development Starter Prompts

A three-stage framework for developing security policies using AI tools, aligned with the four principles of effective AI prompting: Context, Specificity, Structure, and Iteration.

## Overview

These starter prompts guide you through comprehensive policy development in three distinct stages:
1. **Stage 1: Requirements Analysis** - Identify obligations, frameworks, and organizational needs
2. **Stage 2: Control Design** - Develop specific controls, procedures, and implementation guidance
3. **Stage 3: Policy Documentation** - Create formal, stakeholder-appropriate policy documents

Each stage builds on the previous one, allowing verification checkpoints and refinement between stages. This approach ensures policies are compliant, implementable, and aligned with organizational reality.

---

## How to Use These Prompts

1. **Customize the commented sections** (marked with `[MODIFY:]`) based on your organization and policy needs
2. **Execute Stage 1** to analyze requirements and identify gaps
3. **Review the requirements analysis** for completeness and accuracy
4. **Copy Stage 1 output** and use it as input for Stage 2
5. **Verify the control design** is feasible for your organization
6. **Use Stage 2 output** as input for Stage 3
7. **Review the policy documentation** against organizational standards before approval

**Important**: Policy development requires human judgment about risk tolerance, organizational culture, and legal obligations. AI accelerates drafting and ensures comprehensiveness but cannot replace governance decisions.

---

## Stage 1: Requirements Analysis & Framework Mapping

### Purpose
Systematically identify policy requirements from compliance frameworks, regulations, business needs, and industry standards. This stage focuses on understanding what the policy must accomplish without yet designing how to accomplish it.

### The Prompt

```
You are a governance, risk, and compliance (GRC) analyst specializing in regulatory requirements analysis and security framework mapping.

# ROLE CONTEXT [MODIFY: Adjust based on your actual role]
- I am a [MODIFY: "GRC analyst", "Security manager", "Compliance officer", "CISO", "Risk manager"]
- My responsibility includes [MODIFY: "policy development", "compliance management", "security program governance"]
- I report to [MODIFY: "CISO", "Chief Risk Officer", "Chief Compliance Officer", "General Counsel"]
- This policy will be [MODIFY: "new policy creation", "major revision of existing policy", "minor update", "consolidation of multiple policies"]

# ORGANIZATIONAL CONTEXT [MODIFY: Critical for appropriate policy scope]

Industry/Sector: [MODIFY: "Financial Services", "Healthcare", "Technology/SaaS", "Manufacturing", "Retail", "Government", "Education", "Critical Infrastructure"]

Organization Size: [MODIFY: "Small (<500 employees)", "Mid-size (500-5000)", "Large (5000+)", "Enterprise (50,000+)"]

Geographic Operations: [MODIFY: "US only", "North America", "Europe (GDPR applicable)", "Global", "Specific regions: _______"]

Organization Type: [MODIFY: "Public company", "Private company", "Non-profit", "Government agency", "Educational institution"]

# COMPLIANCE & REGULATORY CONTEXT [MODIFY: Drives many policy requirements]

Mandatory Compliance Frameworks:
- [MODIFY: Check all that apply
  - "HIPAA (Healthcare)"
  - "PCI-DSS (Payment cards)"
  - "SOX (Financial reporting)"
  - "GDPR (EU data protection)"
  - "CCPA/CPRA (California privacy)"
  - "GLBA (Financial services)"
  - "FERPA (Education records)"
  - "ITAR/EAR (Export control)"
  - "FedRAMP (Federal cloud)"
  - "CMMC (Defense contractors)"
  - "State-specific regulations: _______"
  - "Industry-specific: _______"
  - "None specific"]

Voluntary Frameworks/Standards:
- [MODIFY: Check frameworks you follow or aspire to
  - "NIST Cybersecurity Framework (CSF)"
  - "ISO 27001/27002"
  - "CIS Controls"
  - "NIST 800-53"
  - "SOC 2 Type II"
  - "PCI-DSS (if not mandatory)"
  - "COBIT"
  - "HITRUST"
  - "Other: _______"]

Contractual Obligations:
- [MODIFY: "Customer security requirements in contracts", "Vendor security standards", "Insurance policy requirements", "None specific"]

# BUSINESS CONTEXT [MODIFY: Shapes policy approach]

Business Model: [MODIFY: "B2B SaaS", "B2C e-commerce", "Financial services", "Healthcare provider", "Manufacturing", "Professional services", "Other: _______"]

Risk Tolerance: [MODIFY: "Low - highly risk-averse", "Moderate - balanced approach", "Higher - accepts more risk for agility"]

Security Maturity: [MODIFY: "Early stage - building program", "Developing - have basics", "Mature - established program", "Advanced - industry-leading"]

Organizational Culture: [MODIFY: "Formal/hierarchical", "Collaborative/consensus-driven", "Fast-moving/startup", "Highly regulated/conservative", "Mixed"]

Technology Environment: [MODIFY: "Cloud-native", "Hybrid cloud", "Primarily on-premises", "Legacy modernization in progress", "Multi-cloud"]

# POLICY SCOPE [MODIFY: Define what policy will cover]

Policy Domain: [MODIFY: Choose one
- "Access Control & Identity Management"
- "Data Protection & Classification"
- "Incident Response & Management"
- "Acceptable Use & User Behavior"
- "Network Security"
- "Cloud Security"
- "Third-Party/Vendor Risk Management"
- "Business Continuity & Disaster Recovery"
- "Vulnerability & Patch Management"
- "Security Awareness & Training"
- "Encryption & Cryptography"
- "Physical Security"
- "Mobile Device Management"
- "Remote Access & Work-from-Home"
- "Change Management"
- "Information Security Program/Master Policy"
- "Data Retention & Disposal"
- "Privacy & Data Handling"
- Custom: "________________________________"]

Policy Scope Boundaries: [MODIFY: What's included/excluded]
- Applies to: [MODIFY: "All employees", "IT staff only", "Specific departments", "Contractors and vendors", "Specific systems/data types"]
- Excludes: [MODIFY: "Certain departments/roles", "Specific systems", "Geographic locations", "Nothing excluded"]
- Related policies: [MODIFY: List policies this will reference or coordinate with]

# EXISTING POLICY STATUS [MODIFY: Important context]

Current State:
- [MODIFY: "No existing policy - creating from scratch"
- "Existing policy needs major revision (last updated: _______)"
- "Existing policy needs minor updates"
- "Multiple policies need consolidation"
- "Policy exists but compliance is poor"]

Known Issues with Current Policy (if exists):
- [MODIFY: "Too technical for business users"
- "Not aligned with current regulations"
- "Doesn't reflect actual practices"
- "Too generic/not specific enough"
- "Conflicts with other policies"
- "Not enforceable"
- "Other: _______"]

# STAKEHOLDER CONTEXT [MODIFY: Who will use/enforce this policy]

Policy Owner: [MODIFY: "CISO", "CIO", "Compliance Officer", "Department head", "To be determined"]

Primary Audience: [MODIFY: "All employees", "IT staff", "Management", "Specific departments", "Mixed audience"]

Enforcement Authority: [MODIFY: "Security team", "HR", "IT operations", "Management", "Multiple groups"]

Approval Required From:
- [MODIFY: List all who must approve: "Executive leadership", "Board/audit committee", "Legal", "Compliance", "Department heads", "InfoSec committee"]

# REQUIREMENTS ANALYSIS INSTRUCTIONS

Analyze and document comprehensive policy requirements:

## 1. REGULATORY & COMPLIANCE REQUIREMENTS

### Mandatory Legal Requirements
For each applicable regulation/framework:
- Regulation name and jurisdiction
- Specific requirements relevant to this policy domain
- Required controls or safeguards
- Documentation requirements
- Audit/reporting obligations
- Penalties for non-compliance
- Citations (specific sections/clauses)

### Framework Control Mapping
Map relevant controls from applicable frameworks:
- Framework name (NIST CSF, ISO 27001, etc.)
- Specific control IDs relevant to this policy
- Control descriptions
- Implementation requirements
- Evidence requirements

### Compliance Gaps
Identify gaps between current state and requirements:
- What's required but not currently addressed
- What's partially addressed but needs strengthening
- What's documented but not enforced
- What's enforced but not documented

## 2. BUSINESS REQUIREMENTS

### Business Objectives
How this policy supports business:
- Business processes this policy protects
- Business risks this policy mitigates
- Operational requirements this policy must accommodate
- Business enablement (not just restriction)

### Risk Management
Risk considerations:
- Key risks this policy must address
- Risk appetite/tolerance considerations
- Residual risks after policy implementation
- Risk trade-offs and balancing

### Operational Constraints
Real-world limitations:
- Technology limitations
- Resource constraints
- Legacy system considerations
- Third-party dependencies
- Timing/phasing requirements

## 3. STAKEHOLDER REQUIREMENTS

### User Requirements
What policy users need:
- Clarity and understandability
- Practical guidance on compliance
- Decision-making support
- Tools and resources needed
- Training requirements

### Enforcer Requirements
What policy enforcers need:
- Clear authority and responsibility
- Measurable compliance criteria
- Violation definitions
- Escalation procedures
- Audit/monitoring approaches

### Management Requirements
What leadership needs:
- Risk visibility
- Compliance status reporting
- Exception handling process
- Resource requirements
- Integration with other governance

## 4. TECHNICAL REQUIREMENTS

### Technical Controls
Required technical implementations:
- Authentication/authorization requirements
- Logging and monitoring
- Encryption requirements
- Network controls
- Endpoint controls
- Cloud security controls
- Backup and recovery
- Technical standards

### Technology Standards
Specific technology requirements:
- Approved tools and technologies
- Configuration standards
- Security baselines
- Integration requirements
- Scalability considerations

## 5. PROCEDURAL REQUIREMENTS

### Operational Procedures
Day-to-day operational needs:
- Standard operating procedures needed
- Workflow requirements
- Approval processes
- Change management integration
- Exception handling
- Documentation requirements

### Administrative Procedures
Governance and oversight:
- Policy review/update cycle
- Compliance monitoring approach
- Violation reporting and response
- Metrics and KPIs
- Training and awareness programs

## 6. INDUSTRY BEST PRACTICES

### Peer Comparison
How similar organizations approach this:
- Industry standard practices
- Common control frameworks
- Lessons learned from peers
- Emerging practices
- What competitors/peers are doing

### Risk-Based Considerations
Threat landscape factors:
- Common attack vectors in this domain
- Industry-specific threats
- Recent incidents/breaches in this area
- Threat actor tactics relevant to policy domain
- Defense-in-depth considerations

## 7. INTEGRATION REQUIREMENTS

### Policy Ecosystem
How this fits with other policies:
- Related policies (reference relationships)
- Dependent policies (must exist first)
- Conflicting policies (need resolution)
- Policy hierarchy (master → sub-policies)
- Standards and procedures that support this policy

### System Integration
Integration with other systems:
- HR systems (onboarding/offboarding)
- IT service management
- GRC platforms
- Monitoring and alerting
- Training/awareness platforms

## 8. REQUIREMENTS PRIORITIZATION

Categorize requirements by priority:

### Must-Have (Mandatory)
- Legal/regulatory requirements (cannot be optional)
- Critical risk mitigations
- Audit requirements
- Board/executive mandates

### Should-Have (Important)
- Industry best practices
- Defense-in-depth measures
- Operational efficiency improvements
- User experience enhancements

### Could-Have (Aspirational)
- Advanced capabilities
- Nice-to-have features
- Long-term maturity goals
- Innovation/leading edge practices

## 9. IMPLEMENTATION CONSIDERATIONS

### Phasing & Timeline
- Can this be implemented all at once or needs phasing?
- What's the realistic timeline?
- What dependencies must be addressed first?
- Quick wins vs. long-term goals?

### Resources Required
- Staff time for implementation
- Technology investments
- Training resources
- Ongoing operational costs
- Change management support

### Change Management
- How big is the change from current state?
- What resistance is anticipated?
- What communication strategy is needed?
- How to gain stakeholder buy-in?

## 10. SUCCESS CRITERIA

Define what success looks like:
- Compliance metrics
- Adoption metrics
- Risk reduction metrics
- User satisfaction indicators
- Audit readiness measures

# OUTPUT FORMAT [MODIFY: Adjust based on needs]

Organization Approach: [MODIFY:
- "Organized by framework (NIST, ISO, etc.)"
- "Organized by requirement type (legal, business, technical)"
- "Organized by priority (must/should/could have)"
- "Narrative flow with integrated requirements"]

Detail Level: [MODIFY: "High detail for implementation planning", "Summary level for executive review", "Balanced approach"]

Structure your requirements analysis:
1. Executive Summary (Key findings, gaps, priorities)
2. Regulatory/Compliance Requirements (by framework)
3. Business Requirements & Risk Considerations
4. Technical Requirements
5. Procedural Requirements
6. Integration & Dependencies
7. Prioritized Requirements (Must/Should/Could)
8. Implementation Roadmap (high-level)
9. Success Criteria
10. Gaps & Recommendations

# CRITICAL INSTRUCTIONS

**ACCURACY REQUIREMENTS:**
- Cite specific regulation sections/clauses (e.g., "HIPAA § 164.312(a)(1)")
- Reference specific framework controls (e.g., "NIST CSF PR.AC-1")
- Do not fabricate compliance requirements
- Flag when you're uncertain about a requirement
- Distinguish between "required by law" vs. "industry best practice"
- Note when regulations have changed recently or are being updated

**COMPLETENESS:**
- Consider all applicable frameworks provided
- Don't skip categories even if they seem less important
- Identify gaps explicitly
- Note areas requiring legal review
- Flag interdependencies between requirements

**PRACTICALITY:**
- Requirements must be implementable in the real world
- Consider organizational constraints provided
- Distinguish "ideal state" from "realistic implementation"
- Note phasing opportunities for large changes
- Consider change management and adoption challenges

**CLARITY:**
- Use precise language for requirements
- Avoid ambiguous terms ("adequate", "reasonable") without definition
- Distinguish "must", "should", and "may" requirements
- Make requirements measurable where possible
- Provide enough detail for next stage (control design)

---

[DESCRIBE YOUR POLICY DEVELOPMENT NEEDS BELOW THIS LINE]

Example: "We need to develop a comprehensive Data Classification and Handling policy for our healthcare SaaS company. We're subject to HIPAA and are pursuing SOC 2 Type II certification. Current state: we have informal practices but no formal policy."

```

---

## Stage 2: Control Design & Implementation Guidance

### Purpose
Transform requirements from Stage 1 into specific security controls, procedures, and implementation guidance. This stage bridges the gap between "what we must do" (requirements) and "how we'll do it" (policy provisions).

### The Prompt

```
You are a security architect and policy designer specializing in translating compliance requirements into implementable security controls and practical procedures.

# ROLE CONTEXT [MODIFY: Your design perspective]
- I am a [MODIFY: "Security architect", "GRC analyst", "Security engineer", "Policy developer"]
- I focus on [MODIFY: "technical control design", "procedure development", "compliance implementation", "risk-based design"]
- I'm designing for [MODIFY: "immediate implementation", "phased rollout", "future state vision"]

# DESIGN CONSTRAINTS [MODIFY: Critical for realistic controls]

Technical Environment:
- Current capabilities: [MODIFY: "Mature enterprise tools (SIEM, EDR, IAM)", "Basic security stack", "Cloud-native tools", "Legacy tools"]
- Planned investments: [MODIFY: "Budget for new tools", "Working with existing tools only", "Major modernization planned"]
- Technical debt: [MODIFY: "Significant legacy systems", "Modern environment", "Mixed modern/legacy"]

Resource Constraints:
- Security team size: [MODIFY: "1-2 people", "Small team (3-10)", "Large team (10+)", "Outsourced"]
- Implementation capacity: [MODIFY: "Limited bandwidth", "Adequate resources", "Dedicated project team"]
- Ongoing operational capacity: [MODIFY: "Minimal ongoing support possible", "Standard operations", "Can sustain complex operations"]

Organizational Constraints:
- Change tolerance: [MODIFY: "Slow to change", "Moderate pace", "Fast-moving/agile"]
- User technical sophistication: [MODIFY: "Non-technical users", "Mixed technical literacy", "Technical organization"]
- Management support: [MODIFY: "Strong executive sponsorship", "Moderate support", "Must justify everything"]

Implementation Timeline:
- Target completion: [MODIFY: "30 days", "90 days", "6 months", "12+ months", "Phased over time"]
- Urgency drivers: [MODIFY: "Regulatory deadline", "Audit finding", "Risk-driven", "Proactive improvement"]
- Phasing acceptable: [MODIFY: "Must implement all at once", "Can phase over time", "Quick wins first, then comprehensive"]

# USER CONTEXT [MODIFY: Who must comply with this policy]

Primary User Groups:
- [MODIFY: List groups: "All employees", "IT staff", "Developers", "Finance team", "Executive team", "Contractors/vendors"]

User Technical Level:
- [MODIFY: "Non-technical business users", "Mixed technical abilities", "Highly technical"]

User Current Behaviors:
- [MODIFY: "Strong security awareness", "Need significant training", "Resistance to security controls expected"]

# ENFORCEMENT CONTEXT [MODIFY: How policy will be enforced]

Enforcement Capability:
- Technical enforcement: [MODIFY: "Can enforce technically (MFA, encryption, etc.)", "Limited technical enforcement", "Primarily procedural"]
- Monitoring capability: [MODIFY: "Comprehensive logging/monitoring", "Basic monitoring", "Manual review only"]
- Audit capability: [MODIFY: "Automated compliance checking", "Periodic manual audits", "Limited audit resources"]

Violation Response:
- Consequences available: [MODIFY: "HR discipline up to termination", "Education/training", "Access revocation", "Management escalation"]
- Enforcement authority: [MODIFY: "Security can enforce directly", "Requires management escalation", "HR-led enforcement"]

Exception Process:
- Exception authority: [MODIFY: "CISO approval", "Risk committee", "Department head", "Formal exception process exists"]
- Exception frequency expected: [MODIFY: "Rare exceptions", "Moderate exceptions", "Many exceptions expected"]

# CONTROL DESIGN INSTRUCTIONS

Using the requirements from Stage 1 (provided below), design comprehensive controls and implementation guidance:

## 1. CONTROL FRAMEWORK DESIGN

### High-Level Control Architecture
Design overall control approach:
- Control philosophy (preventive, detective, corrective balance)
- Defense-in-depth strategy
- Risk-based control prioritization
- Technical vs. administrative control balance
- How controls work together as a system

### Control Categories
Organize controls into logical categories:
- Administrative controls (policies, procedures, training)
- Technical controls (tools, configurations, automation)
- Physical controls (if applicable)
- Personnel controls (background checks, access reviews)

## 2. SPECIFIC CONTROL DESIGN

For each requirement from Stage 1, design specific controls:

### Control Specification Template
For each control:

**Control ID:** [Unique identifier for tracking]
**Control Name:** [Descriptive name]
**Requirement Mapping:** [Which Stage 1 requirements this addresses]
**Framework Mapping:** [NIST CSF, ISO 27001, etc. control IDs]

**Control Type:** [Preventive/Detective/Corrective]
**Implementation Type:** [Technical/Administrative/Physical]

**Control Description:**
- What this control does
- How it mitigates risk
- What it protects against

**Control Owner:** [Who is responsible]
**Control Operator:** [Who implements/maintains]

**Implementation Approach:**
- Specific steps to implement
- Tools or technologies required
- Configuration requirements
- Integration points

**Compliance Criteria:**
- How to verify compliance
- What evidence demonstrates compliance
- Frequency of verification
- Measurement/metrics

**User Impact:**
- How users experience this control
- Workflow changes required
- Potential friction points
- User communication needs

**Exception Handling:**
- When exceptions might be needed
- Exception approval process
- Compensating controls for exceptions
- Exception documentation requirements

**Implementation Timeline:**
- Phase (immediate, short-term, long-term)
- Dependencies (what must happen first)
- Estimated effort
- Risk if delayed

## 3. PROCEDURAL GUIDANCE

### Standard Operating Procedures
For each operational aspect:

**Access Provisioning/Deprovisioning:**
- Step-by-step procedures
- Role definitions and responsibilities
- Approval workflows
- Timeline requirements
- Documentation requirements
- Tools and systems involved

**Monitoring & Detection:**
- What to monitor
- How to monitor (tools, frequency)
- Alert thresholds
- Response procedures for alerts
- Escalation paths
- Logging requirements

**Incident Response:**
- Violation detection and reporting
- Investigation procedures
- Remediation steps
- Documentation requirements
- Post-incident review

**Periodic Reviews:**
- What to review (access rights, configurations, etc.)
- Review frequency
- Review procedures
- Documentation requirements
- Follow-up actions

**Change Management:**
- How policy-related changes are managed
- Change approval process
- Testing requirements
- Rollback procedures

## 4. TECHNICAL IMPLEMENTATION SPECIFICATIONS

### Technology Requirements
For technical controls:

**Authentication/Authorization:**
- MFA requirements (which systems, which users)
- Password standards (length, complexity, rotation)
- Session management (timeout, re-authentication)
- Privileged access management
- Service account management

**Data Protection:**
- Encryption requirements (in-transit, at-rest)
- Key management procedures
- Data classification handling
- Data loss prevention configurations
- Secure data disposal

**Network Security:**
- Network segmentation requirements
- Firewall rules and configurations
- Remote access controls
- VPN requirements
- Wireless security standards

**Endpoint Security:**
- EDR/antivirus requirements
- Device encryption
- Mobile device management
- Patch management timelines
- Secure configuration baselines

**Logging & Monitoring:**
- Log sources required
- Log retention periods
- SIEM integration
- Alert configurations
- Audit trail requirements

**Cloud Security:**
- Cloud security posture management
- Identity and access management
- Data residency requirements
- Cloud service provider requirements
- Multi-cloud considerations

## 5. ROLE-BASED GUIDANCE

### Roles & Responsibilities Matrix

Define specific responsibilities:

| Role | Responsibilities | Authority | Accountability |
|------|-----------------|-----------|----------------|
| [Role name] | [What they must do] | [What they can decide] | [What they're measured on] |

**Key Roles to Define:**
- Policy Owner
- Control Owners
- System Administrators
- End Users
- Security Team
- Compliance Team
- Management
- Third Parties/Vendors

### User Guidance by Role
For each user role:
- What this policy means for them specifically
- Required actions and behaviors
- Prohibited actions
- Decision-making guidance
- Resources and support available
- Consequences for non-compliance

## 6. EXCEPTION & VARIANCE PROCESS

### Exception Criteria
When exceptions are appropriate:
- Business justification requirements
- Risk assessment requirements
- Alternative controls (compensating measures)
- Time-limited vs. permanent exceptions

### Exception Workflow
- Request submission process
- Required documentation
- Approval authority by exception type
- Approval timeline
- Exception tracking and review
- Exception expiration and renewal

### Compensating Controls
For common exception scenarios:
- What compensating controls are acceptable
- How to implement compensating controls
- Monitoring requirements for exceptions
- Documentation requirements

## 7. TRAINING & AWARENESS

### Training Requirements
- Who needs training (all users vs. specific roles)
- Training content outline
- Training delivery method
- Training frequency
- Competency assessment
- Documentation/certification

### Awareness Programs
- Ongoing awareness campaigns
- Communication channels
- Reinforcement techniques
- Measurement of effectiveness

### Documentation & Resources
- User guides and quick reference cards
- FAQ documents
- Self-service resources
- Help desk/support resources

## 8. COMPLIANCE MONITORING

### Monitoring Approach
- Continuous monitoring (automated)
- Periodic assessments (manual)
- Self-assessments
- Third-party audits

### Metrics & KPIs
Define measurable indicators:
- Compliance rate (% users/systems compliant)
- Violation rate and trends
- Exception volume and trends
- Training completion rates
- Incident rates related to policy domain
- Time to remediate violations
- User satisfaction/friction indicators

### Reporting
- Compliance dashboards
- Management reporting frequency
- Board/audit committee reporting
- Regulatory reporting requirements

## 9. CONTINUOUS IMPROVEMENT

### Policy Review & Update
- Review frequency (annual, bi-annual, etc.)
- Trigger events requiring review
- Review process and participants
- Update approval process
- Communication of changes

### Lessons Learned Integration
- Incident analysis feeding policy updates
- Audit finding remediation
- User feedback incorporation
- Technology evolution adaptation
- Threat landscape changes

### Maturity Progression
- Current state assessment
- Target maturity level
- Maturity progression roadmap
- Capability development plan

## 10. IMPLEMENTATION ROADMAP

### Phased Implementation Plan

**Phase 1: Foundation (0-30 days)**
- Quick wins and critical controls
- Minimal user disruption
- Establish baseline

**Phase 2: Core Implementation (30-90 days)**
- Main control deployment
- Procedure establishment
- Initial training rollout

**Phase 3: Enhancement (90-180 days)**
- Advanced controls
- Automation and integration
- Optimization

**Phase 4: Maturity (180+ days)**
- Continuous improvement
- Advanced capabilities
- Full program maturity

### Critical Path
- Dependencies and sequencing
- Blockers and risks
- Resource allocation
- Milestones and checkpoints

### Success Criteria
- Technical implementation complete
- User adoption metrics met
- Compliance targets achieved
- Audit readiness confirmed
- Risk reduction validated

# OUTPUT FORMAT [MODIFY: Adjust based on needs]

Organization Approach: [MODIFY:
- "Organized by control type (technical, administrative, physical)"
- "Organized by implementation phase"
- "Organized by user role"
- "Organized by risk priority"]

Detail Level: [MODIFY: "High technical detail", "Balanced technical and procedural", "Executive summary level"]

Structure your control design:
1. Executive Summary (Approach, priorities, timeline)
2. Control Framework Overview
3. Detailed Control Specifications (organized by chosen approach)
4. Procedural Guidance (SOPs)
5. Technical Implementation Specifications
6. Roles & Responsibilities
7. Exception Process
8. Training & Awareness Plan
9. Compliance Monitoring Approach
10. Implementation Roadmap
11. Appendices (templates, forms, checklists)

# CRITICAL INSTRUCTIONS

**IMPLEMENTABILITY:**
- Every control must be realistic for the constraints provided
- Provide specific, actionable implementation steps
- Consider user experience and change management
- Account for technical limitations
- Phase appropriately for resource constraints

**COMPLETENESS:**
- Address all requirements from Stage 1
- Don't leave gaps in control coverage
- Provide both "what" and "how"
- Include enforcement and monitoring
- Cover exception handling

**MEASURABILITY:**
- Controls must be auditable
- Compliance must be verifiable
- Provide specific metrics
- Define success criteria
- Enable continuous monitoring

**PRACTICALITY:**
- Controls must work in real-world operations
- Balance security with usability
- Consider organizational culture
- Plan for human error and exceptions
- Provide clear guidance for edge cases

**RISK-BASED APPROACH:**
- Prioritize controls by risk reduction
- Allow for risk-based exceptions
- Focus resources on highest risks
- Don't over-control low-risk areas
- Justify control investments

**INTEGRATION:**
- Controls must work together as system
- Integrate with existing processes
- Leverage existing tools where possible
- Consider dependencies
- Avoid redundant or conflicting controls

---

[PASTE THE COMPLETE OUTPUT FROM STAGE 1 BELOW THIS LINE]

```

---

## Stage 3: Policy Documentation & Communication

### Purpose
Transform the control design from Stage 2 into formal, professional policy documentation appropriate for approval, publication, and organizational use. This stage focuses on clarity, authority, and stakeholder-appropriate communication.

### The Prompt

```
You are a policy documentation specialist and security communications expert skilled at creating clear, authoritative, legally sound policy documents.

# AUDIENCE CONTEXT [MODIFY: Critical for appropriate tone and detail]

Primary Readers: [MODIFY:
- "All employees (must read and acknowledge)"
- "Specific departments/roles"
- "Management and leadership"
- "Technical staff"
- "Auditors and regulators"
- Multiple audiences: "________________________"]

Reader Technical Level: [MODIFY: "Non-technical business users", "Mixed technical literacy", "Technical audience"]

Reader Motivation: [MODIFY: "Required compliance", "Voluntary guidance", "Reference document", "Training material"]

# DOCUMENT CONTEXT [MODIFY: Shapes document approach]

Document Purpose: [MODIFY:
- "Enforceable policy (violations have consequences)"
- "Guidance document (best practices)"
- "Standard (technical specifications)"
- "Procedure (step-by-step instructions)"
- Combined policy with procedures]

Document Authority: [MODIFY:
- "Board-approved policy"
- "Executive leadership policy"
- "Department policy"
- "Technical standard"]

Approval Required From:
- [MODIFY: "Board/Audit Committee", "Executive team", "Legal", "Compliance", "CISO", "Department heads"]

Legal Review Required: [MODIFY: Yes/No]

# ORGANIZATIONAL STANDARDS [MODIFY: Your documentation requirements]

Policy Numbering/Naming: [MODIFY: "Use existing convention: _______", "Create new convention", "No specific requirement"]

Document Template: [MODIFY: "Must use corporate template", "Flexible format", "Follow previous policy format"]

Policy Structure Requirements: [MODIFY:
- "Must follow corporate policy format"
- "Must include specific sections: _______"
- "Flexible structure"
- "Follow industry standard structure"]

Writing Style Guide: [MODIFY: "Follow corporate style guide", "Professional business writing", "Plain language preferred", "Technical precision required"]

Accessibility Requirements: [MODIFY: "Must be ADA compliant", "Plain language (8th-grade reading level)", "Multiple language versions needed", "Standard business document"]

# PUBLICATION CONTEXT [MODIFY: How policy will be distributed]

Distribution Method:
- [MODIFY: "Intranet/policy portal", "Email distribution", "Training platform", "Physical distribution", "Multiple channels"]

Acknowledgment Required: [MODIFY: Yes/No]
- If yes: [MODIFY: "Electronic signature", "Annual re-acknowledgment", "Role-based acknowledgment"]

Version Control: [MODIFY: "Formal version control required", "Simple versioning", "Track changes important", "Not critical"]

# SUPPLEMENTARY DOCUMENTS [MODIFY: What else is needed]

Supporting Documents Needed:
- [MODIFY: Select all that apply
  - "Standards (technical specifications)"
  - "Procedures (step-by-step guides)"
  - "Guidelines (best practices)"
  - "Job aids/quick reference cards"
  - "Training materials"
  - "FAQ document"
  - "Forms and templates"
  - "Compliance checklist"
  - "Implementation guide"
  - "Executive summary"
  - "User guide"]

Relationship to Other Policies:
- [MODIFY: "References these policies: _______"
- "Supersedes these policies: _______"
- "Related to these policies: _______"
- "Standalone policy"]

# POLICY DOCUMENTATION INSTRUCTIONS

Using the control design from Stage 2 (provided below), create comprehensive policy documentation:

## 1. POLICY HEADER & METADATA

**Document Information:**
- Policy Title: [Clear, descriptive]
- Policy Number: [Per organizational convention]
- Version: [X.X]
- Effective Date:
- Next Review Date:
- Supersedes: [Previous version or policies replaced]
- Owner: [Title, not name]
- Approver: [Title, not name]

**Distribution:**
- Applies to: [Specific scope]
- Exceptions: [If any]
- Classification: [Public/Internal/Confidential]

## 2. EXECUTIVE SUMMARY [MODIFY: Length based on audience]

Create a [MODIFY: "One paragraph", "Half page", "Full page"] summary including:
- Purpose of this policy (why it exists)
- Scope (who and what it covers)
- Key requirements (3-5 main points)
- Compliance expectations
- Effective date and transition plan

**Tone:** [MODIFY: "Formal and authoritative", "Professional but accessible", "Plain language"]

## 3. PURPOSE & OBJECTIVES

**Policy Purpose:**
- Why this policy exists
- Problems it solves
- Risks it mitigates
- Value it provides

**Policy Objectives:**
- What this policy will accomplish
- Expected outcomes
- Success metrics (if appropriate)

**Regulatory Context:**
- Compliance obligations this policy meets
- Regulatory references (HIPAA, PCI-DSS, etc.)
- Audit/regulatory expectations

## 4. SCOPE & APPLICABILITY

**Scope Statement:**
Define clearly and explicitly:
- Who must comply (employees, contractors, vendors, etc.)
- What systems/data/processes are covered
- Geographic scope
- Temporal scope (when it applies)

**Exclusions:**
- What is explicitly NOT covered
- Why exclusions exist
- Where excluded items are covered (if elsewhere)

**Related Policies:**
- Policies that work together with this one
- Hierarchical relationships (parent/child policies)
- Cross-references

## 5. DEFINITIONS

**Key Terms:**
Define terms that may be ambiguous or technical:
- Use plain language definitions
- Define acronyms
- Clarify organizational-specific terminology
- Define roles mentioned in policy
- Explain technical concepts for non-technical readers

**Avoid:**
- Overly technical definitions
- Circular definitions
- Assumed knowledge

## 6. POLICY STATEMENTS

This is the core authoritative content. Structure as:

### A. HIGH-LEVEL POLICY PRINCIPLES

State overarching principles (3-5 statements):
- "The organization shall..." statements
- Mandatory requirements using "must" or "shall"
- Fundamental security principles
- Risk-based approach
- Defense-in-depth philosophy

### B. SPECIFIC REQUIREMENTS

For each control area from Stage 2, create policy statements:

**Format:**
- Use imperative language ("must", "shall", "will")
- Be specific but not overly prescriptive
- State WHAT is required, not HOW (save HOW for procedures)
- Make requirements measurable/auditable
- Use numbered or lettered sections for easy reference

**Organization:** [MODIFY: Choose approach
- "By control category (access control, data protection, etc.)"
- "By user role"
- "By system/data type"
- "By risk level"
- "Chronological (procurement to disposal)"]

**Example Structure:**

**6.1 Access Control Requirements**

6.1.1 Authentication
- Users MUST authenticate using multi-factor authentication for [specific systems/scenarios]
- Passwords MUST meet [specific standards or reference to standard]
- Sessions MUST timeout after [X] minutes of inactivity

6.1.2 Authorization
- Access MUST be granted based on principle of least privilege
- Access reviews MUST be conducted [frequency]
- Privileged access MUST be [specific requirements]

**6.2 Data Protection Requirements**

6.2.1 Data Classification
- All data MUST be classified as [classification scheme]
- Classification MUST be determined by [criteria]
- Handling requirements MUST align with classification

6.2.2 Encryption
- Data classified as [level] MUST be encrypted in transit using [standard]
- Data classified as [level] MUST be encrypted at rest using [standard]

[Continue for each control area]

### C. ROLES & RESPONSIBILITIES

**Clearly Define:**
- Policy Owner: [Responsibilities]
- Executive Leadership: [Responsibilities]
- Security Team: [Responsibilities]
- IT Operations: [Responsibilities]
- Business Unit Leaders: [Responsibilities]
- Individual Users: [Responsibilities]
- Vendors/Third Parties: [Responsibilities]

**Format:**
- Use table format or clearly structured lists
- Distinguish between responsibility, authority, and accountability
- Make responsibilities specific and actionable

## 7. COMPLIANCE & ENFORCEMENT

### Compliance Requirements
- How compliance is measured
- Compliance monitoring approach
- Self-assessment requirements
- Audit requirements
- Reporting requirements

### Exceptions Process
- When exceptions are permitted
- How to request exceptions
- Who approves exceptions
- Exception documentation requirements
- Exception review and expiration

### Violations & Consequences
- What constitutes a violation
- Violation reporting requirements
- Investigation process
- Range of consequences (education to termination)
- Appeal process (if applicable)

**Tone Guidance:**
- Be firm but not threatening
- Focus on importance of compliance
- Acknowledge that violations may be inadvertent
- Emphasize support available for compliance
- Be clear about serious consequences for willful violations

## 8. POLICY GOVERNANCE

### Policy Review & Updates
- Review frequency (annual, bi-annual)
- Review process and participants
- Triggers for ad-hoc review
- Update approval process
- Communication of changes

### Policy Owner Responsibilities
- Maintaining policy currency
- Ensuring implementation
- Monitoring compliance
- Providing guidance and interpretation
- Coordinating training

### Version Control
- How versions are numbered
- Change documentation requirements
- Archive policy for superseded versions

## 9. REFERENCES

### Internal References
- Related policies
- Standards and procedures
- Forms and templates
- Training materials
- Contact information for questions

### External References
- Regulatory citations (specific sections)
- Framework references (NIST CSF, ISO 27001)
- Industry guidelines
- Legal requirements

### Resources & Support
- Where to get help
- Training resources
- Tools available
- Policy interpretation guidance

## 10. APPENDICES [MODIFY: As needed]

### Appendix A: Acronyms & Glossary
- Comprehensive list of acronyms
- Glossary of technical terms

### Appendix B: Roles & Responsibilities Matrix
- Detailed RACI matrix

### Appendix C: Implementation Timeline
- Phased implementation schedule
- Transition plan for legacy systems/processes

### Appendix D: Compliance Checklist
- User-facing compliance checklist
- Department-level compliance checklist
- Audit checklist

### Appendix E: Templates & Forms
- Exception request form
- Access request form
- Incident reporting form
- Other relevant templates

### Appendix F: Technical Standards
- Detailed technical specifications
- Configuration requirements
- Approved tools/technologies

### Appendix G: Frequently Asked Questions
- Common questions and answers
- Scenario-based guidance

## 11. DOCUMENT HISTORY

Track changes over time:

| Version | Date | Author | Changes | Approver |
|---------|------|--------|---------|----------|
| 1.0 | [Date] | [Role] | Initial release | [Approver] |

# SUPPLEMENTARY DOCUMENT INSTRUCTIONS

For each supporting document needed (from context above):

## STANDARDS Document (Technical Specifications)

If creating a technical standard:
- More prescriptive than policy
- Specific technical requirements
- Configuration details
- Approved technologies
- Technical procedures
- Reference architecture
- Security baselines

## PROCEDURES Document (Step-by-Step)

If creating procedures:
- Numbered step-by-step instructions
- Process flowcharts
- Decision trees
- Screenshots or diagrams
- Troubleshooting guidance
- Forms and templates to use

## GUIDELINES Document (Best Practices)

If creating guidelines:
- Recommended approaches
- Best practices
- Tips and techniques
- Context-specific guidance
- "Should" rather than "must" language

## QUICK REFERENCE Cards

User-facing quick guides:
- One-page or two-sided card
- Key do's and don'ts
- Common scenarios
- Where to get help
- Visual/graphical format

## USER GUIDE

Comprehensive user documentation:
- Organized by common tasks
- Screenshots and examples
- Troubleshooting section
- FAQ section
- Contacts for support

## EXECUTIVE SUMMARY

For senior leadership:
- 1-2 page maximum
- Business risk context
- Key requirements overview
- Resource requirements
- Implementation timeline
- Success metrics
- Board presentation format

## TRAINING MATERIALS

For security awareness:
- Training presentation outline
- Key learning objectives
- Assessment questions
- Scenario-based exercises
- Completion criteria

# OUTPUT FORMAT [MODIFY: Choose appropriate format]

Primary Document Format: [MODIFY:
- "Formal policy document (traditional structure)"
- "Plain language policy (accessible format)"
- "Interactive/web-based policy"
- "Combined policy with integrated procedures"
- "Modular policy (sections can stand alone)"]

Length Guidance: [MODIFY:
- "Concise (5-10 pages)"
- "Comprehensive (15-25 pages)"
- "As long as needed for complete coverage"
- "Minimal viable policy (short as possible)"]

Visual Elements: [MODIFY:
- "Include flowcharts for processes"
- "Include decision trees"
- "Include tables and matrices"
- "Include diagrams for complex concepts"
- "Text only - minimal formatting"]

Formatting Standards: [MODIFY:
- "Corporate template formatting"
- "Professional business document"
- "ADA-compliant formatting"
- "Web-ready format"
- "Print-ready format"]

# WRITING STYLE GUIDELINES

**Tone:** [MODIFY: "Formal and authoritative", "Professional but approachable", "Plain language focus", "Technical precision"]

**Language:**
- Use active voice ("Users must" not "Must be done by users")
- Use "must" or "shall" for requirements, "should" for recommendations
- Be specific and unambiguous
- Define acronyms on first use
- Use consistent terminology throughout
- Write for your audience's comprehension level

**Structure:**
- Use hierarchical numbering for easy reference
- Keep paragraphs short and focused
- Use bullet points for lists
- Use tables for complex information
- Include white space for readability

**Avoid:**
- Jargon without definition
- Overly technical language for non-technical audience
- Ambiguous terms ("reasonable", "appropriate" without definition)
- Passive voice
- Run-on sentences
- Walls of text without structure

# CRITICAL INSTRUCTIONS

**AUTHORITY & CLARITY:**
- Policy language must be clear and authoritative
- Requirements must be unambiguous
- "Must" means mandatory, "Should" means recommended
- Avoid softening language that undermines authority
- Be definitive where requirements are definitive

**LEGAL SOUNDNESS:**
- Ensure policy is legally enforceable
- Avoid language that creates unintended obligations
- Be consistent with employment law
- Consider union agreements if applicable
- Flag sections needing legal review

**AUDITABILITY:**
- Every requirement should be auditable
- Compliance should be objectively measurable
- Evidence requirements should be clear
- Avoid requirements that can't be verified

**USABILITY:**
- Write for the actual users who must comply
- Provide context and rationale (helps with buy-in)
- Include examples for complex requirements
- Make it easy to find relevant sections
- Provide resources for questions

**CONSISTENCY:**
- Use consistent terminology throughout
- Reference related policies consistently
- Align with other organizational policies
- Use consistent formatting and structure
- Maintain consistent tone

**COMPLETENESS:**
- Address all control areas from Stage 2
- Include all required sections
- Provide sufficient detail for implementation
- Don't leave ambiguity in critical areas
- Include all necessary supporting documents

---

[PASTE THE COMPLETE OUTPUT FROM STAGE 2 BELOW THIS LINE]

```

---

## Iteration Guidance

### When to Iterate at Each Stage

**Stage 1 Iteration Triggers:**
- Requirements analysis too generic for your regulations
- Missing critical compliance frameworks
- Doesn't capture your organizational constraints
- Stakeholder requirements unclear or incomplete
- Integration requirements not addressed
- Prioritization doesn't match your risk model

**Stage 2 Iteration Triggers:**
- Controls not implementable with your resources
- Technical specifications don't match your environment
- Procedures too complex for your organization
- User impact not adequately addressed
- Exception process unclear or unworkable
- Implementation timeline unrealistic
- Doesn't align with organizational culture

**Stage 3 Iteration Triggers:**
- Wrong tone or formality level for your organization
- Policy structure doesn't match organizational standards
- Language too technical or too simplified for audience
- Missing required sections or metadata
- Supplementary documents insufficient
- Writing style doesn't match organizational voice
- Legal or compliance concerns with language

### Effective Refinement Prompts

**To Add Specificity:**
"Provide more detailed requirements for [specific framework/regulation]. Include specific control IDs and citations for [HIPAA/PCI-DSS/etc.]"

**To Adjust for Constraints:**
"The controls you designed for [area] won't work in our environment because [reason]. Redesign these controls considering [specific constraint]."

**To Simplify:**
"This policy is too complex for our users. Simplify [section] to 8th-grade reading level while maintaining technical accuracy and compliance requirements."

**To Add Missing Elements:**
"You didn't address [specific requirement/scenario]. Add provisions for [describe need] that comply with [framework/regulation]."

**To Adjust Tone:**
"The tone in [section] is too [harsh/soft/technical]. Rewrite with [appropriate tone] while maintaining [authority/clarity/accessibility]."

### When to Start Fresh

- After 3-4 iterations without meaningful improvement
- When fundamental assumptions about your organization were wrong
- When compliance requirements change mid-development
- When stakeholder feedback requires complete redesign
- When organizational priorities shift significantly

---

## Verification Requirements

### Critical Verification Steps

**Stage 1 Verification:**
- ✅ Verify regulatory citations are accurate (specific sections, current versions)
- ✅ Check framework control mappings against actual frameworks
- ✅ Confirm requirements align with your actual compliance obligations
- ✅ Validate business requirements with stakeholders
- ✅ Verify organizational constraints are accurately captured
- ✅ Confirm prioritization aligns with risk assessment

**Stage 2 Verification:**
- ✅ Validate controls are technically feasible in your environment
- ✅ Confirm procedures align with existing operational processes
- ✅ Check technical specifications against your tools/capabilities
- ✅ Verify implementation timeline is realistic
- ✅ Validate resource estimates with those who will implement
- ✅ Confirm exception process aligns with governance structure

**Stage 3 Verification:**
- ✅ Legal review for enforceability and compliance
- ✅ Compliance review for regulatory alignment
- ✅ Stakeholder review for clarity and usability
- ✅ Technical review for accuracy of specifications
- ✅ User testing for comprehension (if possible)
- ✅ Formatting review against organizational standards

### Red Flags Requiring Extra Scrutiny

**🚩 Requirements Issues:**
- Generic requirements that could apply to any organization
- Compliance requirements without specific citations
- "Best practices" presented as legal requirements
- Conflicting requirements from different frameworks
- Requirements that ignore stated organizational constraints

**🚩 Control Design Issues:**
- Controls that require tools/capabilities you don't have
- Procedures that don't integrate with existing workflows
- Exception processes with unclear authority
- User impacts that will cause major resistance
- Implementation timelines that ignore dependencies

**🚩 Documentation Issues:**
- Ambiguous language that could be interpreted multiple ways
- Requirements using "should" when they must be mandatory
- Missing definitions for critical terms
- Inconsistent terminology across sections
- Unenforceability due to language choices

### Verification Resources

**Regulatory Verification:**
- Actual regulation text (not summaries)
- Compliance framework documentation
- Legal counsel review
- Industry compliance resources
- Regulatory guidance documents

**Technical Verification:**
- Security architects for technical feasibility
- IT operations for operational feasibility
- System administrators for implementation details
- Tool vendors for capability verification

**Organizational Verification:**
- HR for personnel policies and consequences
- Legal for enforceability
- Compliance for regulatory alignment
- Department leaders for operational impact
- Executive sponsor for authority and approval

---

## Use Case Examples

### Example 1: Healthcare Data Classification Policy

**Stage 1 Focus:**
- HIPAA requirements for PHI protection
- State breach notification laws
- Business associate requirements
- Data lifecycle from creation to disposal
- Integration with existing privacy policies

**Stage 2 Focus:**
- Classification scheme (PHI vs. non-PHI)
- Handling requirements by classification
- Technical controls (encryption, access control)
- Business associate agreements
- Breach notification procedures

**Stage 3 Focus:**
- Clear policy defining PHI
- User guidance for classification decisions
- Technical standards for protection
- Procedure for handling PHI
- Quick reference guide for common scenarios

### Example 2: Access Control Policy for Financial Services

**Stage 1 Focus:**
- SOX requirements for financial systems
- PCI-DSS for payment card data
- GLBA for customer financial information
- Industry best practices (privileged access management)
- Regulatory exam expectations

**Stage 2 Focus:**
- Role-based access control design
- Privileged access management procedures
- Access review requirements
- Technical implementation (MFA, PAM tools)
- Segregation of duties enforcement

**Stage 3 Focus:**
- Formal access control policy
- Access request procedures
- Access review procedures
- Technical standards for authentication
- Compliance monitoring procedures

### Example 3: Cloud Security Policy for SaaS Startup

**Stage 1 Focus:**
- SOC 2 Type II requirements
- Customer contractual obligations
- Cloud service provider (CSP) shared responsibility
- Rapid growth and scaling needs
- Limited security team resources

**Stage 2 Focus:**
- Cloud security posture management
- Identity and access management in cloud
- Data protection in cloud environments
- Third-party cloud service vetting
- Monitoring and logging in cloud

**Stage 3 Focus:**
- Cloud security policy
- Cloud service approval procedure
- Technical standards for cloud configuration
- Shared responsibility matrix
- Cloud incident response procedures

---

## Policy Lifecycle Management

### Post-Development Activities

**Implementation:**
1. Gain final approvals
2. Communicate policy rollout
3. Conduct training
4. Deploy technical controls
5. Establish monitoring
6. Begin enforcement

**Monitoring:**
1. Track compliance metrics
2. Monitor violations
3. Review exception requests
4. Gather user feedback
5. Assess effectiveness

**Maintenance:**
1. Periodic reviews (annual/bi-annual)
2. Update for regulatory changes
3. Incorporate lessons learned
4. Adapt to technology changes
5. Refresh training content

**Continuous Improvement:**
1. Analyze compliance trends
2. Benchmark against peers
3. Assess control effectiveness
4. Optimize based on feedback
5. Mature over time

### Policy Relationships

**Policy Hierarchy:**
- Information Security Program (Master Policy)
  - Domain Policies (Access Control, Data Protection, etc.)
    - Standards (Technical specifications)
      - Procedures (Step-by-step instructions)
        - Guidelines (Best practices)

**Integration Points:**
- HR policies (onboarding, termination, discipline)
- IT policies (change management, incident management)
- Business policies (procurement, vendor management)
- Legal policies (contracts, records retention)
- Privacy policies (data handling, consent)

---

## Customization for Different Policy Types

### Access Control & Identity Management
- Heavy emphasis on authentication/authorization requirements
- Role-based access control design
- Privileged access management
- Access review procedures
- Integration with HR processes

### Data Protection & Classification
- Data classification schemes
- Handling requirements by classification
- Encryption requirements
- Data lifecycle management
- Privacy considerations

### Incident Response
- Incident definitions and categories
- Response procedures and playbooks
- Escalation paths
- Communication protocols
- Post-incident review

### Third-Party Risk Management
- Vendor assessment requirements
- Contract requirements
- Ongoing monitoring
- Incident response coordination
- Data protection requirements

### Cloud Security
- Shared responsibility model
- Cloud service approval process
- CSP security requirements
- Cloud configuration standards
- Multi-cloud considerations

---

## Best Practices

### Context Best Practices

✅ **Do:**
- Be specific about all applicable regulations
- Accurately describe organizational constraints
- Identify all stakeholders who must approve/use policy
- Describe your actual environment, not ideal state

❌ **Don't:**
- Assume AI knows your regulatory environment
- Skip organizational culture considerations
- Ignore resource constraints
- Provide generic industry without specifics

### Specificity Best Practices

✅ **Do:**
- Name specific regulations and cite specific sections
- Define target reading level for policy
- Specify required approval authorities
- Identify all supporting documents needed

❌ **Don't:**
- Ask for "a security policy" without domain specification
- Leave compliance frameworks vague
- Skip audience definition
- Assume AI knows your documentation standards

### Structure Best Practices

✅ **Do:**
- Use three-stage separation (Requirements → Controls → Documentation)
- Verify between stages with appropriate stakeholders
- Build iteratively from requirements through documentation
- Allow time for legal/compliance review

❌ **Don't:**
- Try to write policy without requirements analysis
- Skip control design and jump to policy writing
- Rush through stages without verification
- Combine stages into single massive prompt

### Iteration Best Practices

✅ **Do:**
- Iterate based on stakeholder feedback
- Refine for your specific organizational context
- Test policy language with actual users
- Adjust for compliance requirement changes

❌ **Don't:**
- Accept generic policy language
- Iterate without clear objectives
- Continue past diminishing returns
- Ignore fundamental feasibility issues

---

## Troubleshooting

### Common Issues & Solutions

**Issue:** Requirements too generic, don't address your specific regulations
**Solution:** In Stage 1, add: "I need specific citations to [regulation name] sections that apply to [policy domain]. Include exact section numbers and requirement text. Don't provide generic compliance guidance."

**Issue:** Controls require tools or capabilities you don't have
**Solution:** In Stage 2, add detailed technical constraints: "We use [specific tools]. We do NOT have [specific capabilities]. All controls must be implementable with existing tools or explicitly identify required new tools with justification."

**Issue:** Policy language too technical for your audience
**Solution:** In Stage 3, specify: "This policy will be read by [specific audience with reading level]. Use plain language at [grade level]. Define all technical terms. Provide examples for complex concepts."

**Issue:** Policy doesn't match organizational writing style
**Solution:** In Stage 3, provide examples: "Our policies use this tone: [provide sample]. Match this style, including [specific elements like formality level, use of contractions, headers style, etc.]"

**Issue:** Missing critical compliance requirements
**Solution:** Enhance Stage 1: "Review [specific regulation] sections [list sections] and identify ALL requirements related to [policy domain]. Include requirements for documentation, audit, reporting, breach notification, etc."

**Issue:** Implementation timeline unrealistic
**Solution:** In Stage 2, add: "We have [X] staff available [Y] hours per week. Implementation must be phased over [timeframe]. Identify dependencies and create realistic timeline considering [specific constraints]."

---

## Security & Privacy Considerations

### Before Using These Prompts

**✅ DO:**
- Use enterprise AI instances with data protection agreements
- Sanitize specific organizational vulnerabilities
- Verify all regulatory citations before final policy
- Have legal review before publication
- Validate controls are technically accurate
- Test policy comprehension with actual users

**❌ DON'T:**
- Include specific unpatched vulnerabilities
- Share details of past security incidents without sanitization
- Include actual user data or sensitive examples
- Trust regulatory guidance without verification
- Skip legal review for enforceable policies
- Publish policy without stakeholder approval

### Information Handling Classifications

**Suitable for AI (with enterprise instances):**
- General regulatory requirements (public information)
- Industry-standard control frameworks
- Generic organizational structure
- Common business processes
- Standard technical architectures (abstracted)

**Requires Sanitization:**
- Specific security gaps
- Organizational risk assessments
- Resource constraints and limitations
- Past incident details
- Vendor names and tool specifics (when sensitive)

**Should NOT Use AI:**
- Specific active vulnerabilities
- Detailed threat intelligence about your organization
- Legal opinions or advice
- Contract-specific obligations (without legal review)
- Merger/acquisition information

---

## Template Management

### Version Control Best Practices

```
# Security Policy Template v1.0
# Policy Domain: [Access Control/Data Protection/etc.]
# Last Updated: 2024-11-06
# Tested For: [Organization types, compliance frameworks]
# Status: [Draft/In Review/Approved/Published]
# Next Review: 2025-11-06
```

### Organization Structure

```
/security-policies/
  /templates/
    /stage-1-requirements/
    /stage-2-controls/
    /stage-3-documentation/
  /approved-policies/
  /standards/
  /procedures/
  /guidelines/
  /training-materials/
```

### Knowledge Management

**Capture Lessons Learned:**
- Which frameworks are most relevant
- Common stakeholder feedback patterns
- Effective control designs for your environment
- Writing styles that work well with your audience
- Regulatory interpretation challenges

**Build Organizational Library:**
- Reusable control libraries
- Standard policy language
- Approved terminology
- Common procedure templates
- Training content modules

---

## Contributing

Help improve these prompts:
1. Share successful policy development approaches
2. Document effective regulatory mappings
3. Contribute control design patterns
4. Share stakeholder engagement strategies
5. Provide writing style examples

---

## License & Attribution

[Add your license]

Based on the four principles framework from "Prompt Thinking for Security Professionals" - Context, Specificity, Structure, and Iteration.

Aligned with governance best practices and regulatory compliance frameworks.

---

## Additional Resources

**Compliance Frameworks:**
- NIST Cybersecurity Framework: https://www.nist.gov/cyberframework
- ISO 27001/27002: https://www.iso.org/isoiec-27001-information-security.html
- CIS Controls: https://www.cisecurity.org/controls
- NIST 800-53: https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final

**Regulatory Resources:**
- HIPAA: https://www.hhs.gov/hipaa
- PCI-DSS: https://www.pcisecuritystandards.org
- GDPR: https://gdpr.eu
- State Privacy Laws: [Various state attorney general sites]

**Policy Writing Resources:**
- SANS Policy Templates: https://www.sans.org/information-security-policy/
- NIST Policy Guidance: https://csrc.nist.gov
- Plain Language Guidelines: https://www.plainlanguage.gov

---

**Remember**: Policy development is fundamentally a governance activity requiring human judgment about risk tolerance, organizational culture, and legal obligations. AI accelerates the analysis, design, and documentation phases but cannot replace the strategic decisions and stakeholder engagement that make policies effective. Use these prompts to build comprehensive, compliant, implementable policies faster - but always apply critical thinking and organizational context throughout the process.
