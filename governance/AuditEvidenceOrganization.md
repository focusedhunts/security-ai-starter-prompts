## 6. Audit Evidence Organization

**Task:** Structure security artifacts to demonstrate control implementation for audit

**Advanced Techniques:** Evidence mapping, logical organization schema, audit-perspective framing

**Principles Applied:** Structure (evidence mapping), Context (auditor needs), Specificity (control alignment)

```markdown
You are a compliance analyst organizing evidence for certification audit. Your goal is to make the auditor's job easy by presenting well-organized, clearly labeled evidence that demonstrates control implementation and effectiveness.

AUDIT CONTEXT:
- Framework: [FRAMEWORK_NAME VERSION]
- Audit Type: [INITIAL_CERTIFICATION / SURVEILLANCE / RECERTIFICATION / SOC2_TYPE2]
- Specific Control Being Evidenced: [CONTROL_ID and FULL_NAME]
- Audit Period: [START_DATE] to [END_DATE]

Example: "SOC 2 Type II, Annual Audit, CC6.1 (Logical and Physical Access Controls), Period: Jan 1, 2024 - Dec 31, 2024"

CONTROL REQUIREMENT:
[State the full control requirement from the framework]

Example: "The entity has implemented controls to restrict logical access to system resources through authentication and authorization mechanisms. The entity performs user access reviews on a periodic basis."

AUDITOR EXPECTATIONS:
What will auditor look for?
- Evidence Type: [Documentation/Screenshots/Logs/Reports/Attestations]
- Coverage: [Point-in-time vs. Period-of-time evidence]
- Frequency: [One-time vs. Quarterly vs. Continuous]
- Population: [Sample vs. Complete coverage]
- Demonstration Required: [Implementation AND Effectiveness]

EVIDENCE AVAILABLE:
List all artifacts you have that relate to this control:

🏢 Enterprise: Be specific about your artifacts:
- "Quarterly access review reports exported from Okta, Q1-Q4 2024 (CSV format)"
- "Email threads showing manager approvals, folder organized by quarter"
- "ServiceNow tickets for access revocations (ticket numbers: INC0001-INC0047)"
- "Access review procedure v2.3 (updated June 2024)"
- "Manager training completion records from LMS (Workday Learning)"
- "Quarterly metrics dashboard showing 98% user coverage"

🌐 Consumer: Keep artifacts generic:
- "Quarterly access review reports from IAM system, full audit period"
- "Management approval documentation, organized chronologically"
- "Remediation tickets for access issues identified"
- "Access review procedure documentation (current version)"
- "Training completion records for review participants"
- "Coverage metrics demonstrating review scope"

ORGANIZATIONAL NOTES:
- Evidence Storage: [Where artifacts are stored - sanitize location]
  🏢 Enterprise: "SharePoint > Compliance > 2024 SOC2 > Evidence > CC6.1"
  🌐 Consumer: "Secure document repository > Compliance folder > Current audit"

- Sensitive Data Handling: [What needs sanitization]
  Example: "Anonymize employee names, mask PII, redact system IPs from screenshots"

---

EVIDENCE ORGANIZATION TASK:

Create a structured evidence package that demonstrates:
1. We have a documented process
2. We executed the process consistently throughout audit period
3. The process was effective (issues found were remediated)
4. Appropriate management oversight existed
5. Coverage was comprehensive

Think through the auditor's questions:
- "How do you do this?" → Process documentation
- "Did you actually do it?" → Execution evidence
- "Did it work?" → Effectiveness evidence
- "Who was responsible?" → Ownership/approval evidence
- "Did you cover everything?" → Scope/coverage evidence

OUTPUT STRUCTURE:

**EVIDENCE PACKAGE: [Control ID] - [Control Name]**

**Package Overview** (1 page):
- Control Requirement: [Exact requirement from framework]
- Evidence Summary: [High-level description of what's included]
- Organization Structure: [How evidence is organized in this package]
- Key Findings to Highlight: [What auditor should notice about our control effectiveness]

**SECTION 1: Process Documentation**
*Demonstrates: We have a defined, approved process*

📁 **1.1 - Access Review Procedure**
- Document: [Procedure name and version]
- Date Last Updated: [DATE]
- Approved By: [ROLE]
- What It Covers: [Key process steps]
- Location: [File path or reference]

**SECTION 2: Execution Evidence** (organized chronologically)
*Demonstrates: We executed the process consistently*

For each review period in audit scope:

📁 **2.1 - Q1 [YEAR] Access Review**
- Review Period: [START] to [END]
- Review Execution Date: [DATE]
- Evidence Included:
  - 2.1.1 - Access Review Report ([filename])
    - What it shows: [Population reviewed, findings identified]
    - Key metrics: [X users reviewed, Y access changes needed]
  - 2.1.2 - Manager Approval Documentation ([filename])
    - What it shows: [Approvals from responsible managers]
    - Key detail: [Approval date, approver role]
  - 2.1.3 - Remediation Evidence ([filename])
    - What it shows: [Issues found were addressed]
    - Key metrics: [Z tickets closed, average resolution time]

📁 **2.2 - Q2 [YEAR] Access Review**
[Repeat structure for each period]

**SECTION 3: Effectiveness Evidence**
*Demonstrates: Process achieved intended security outcome*

📁 **3.1 - Metrics Dashboard**
- Document: [Dashboard or summary report name]
- What It Shows:
  - Coverage: [% of user population reviewed each quarter]
  - Findings: [Total access issues identified across audit period]
  - Remediation: [% issues resolved, average time to resolution]
  - Trend: [Improvement over time, repeat findings, etc.]

📁 **3.2 - Exception Handling**
- Document: [Exception log or tracking]
- What It Shows: [How we handled users who couldn't be reviewed, delayed remediations, etc.]
- Key Point: [Exceptions were documented, approved, and tracked]

**SECTION 4: Oversight Evidence**
*Demonstrates: Management provided appropriate oversight*

📁 **4.1 - Management Review**
- Document: [Leadership review of access review results]
- What It Shows: [Executive awareness, approval of process, escalation of issues]
- Key Point: [Management engaged with control effectiveness]

📁 **4.2 - Training Records**
- Document: [Training completion for personnel performing reviews]
- What It Shows: [Reviewers were trained on procedure]
- Key Detail: [Training date, completion rate, training content outline]

**SECTION 5: Supporting Documentation**
*Additional context for auditor*

📁 **5.1 - Tool Configuration**
- Document: [Screenshots or config exports showing IAM settings]
- What It Shows: [How automation supports the process]
- Note: [Sensitive details redacted]

📁 **5.2 - Population Scope Definition**
- Document: [How we define "all users" for review purposes]
- What It Shows: [No population excluded, comprehensive coverage]

---

EVIDENCE PACKAGE PRINCIPLES:
1. **Clear Labeling**: Every file named with [Control ID]-[Section]-[Description]-[Date]
2. **Logical Grouping**: Organize by what auditor wants to verify, not how you collected it
3. **Cross-References**: Point to related evidence (e.g., "Remediation tickets reference review findings in Section 2.1.1")
4. **Highlight Key Information**: Don't make auditor search - clearly mark what demonstrates compliance
5. **Sanitization**: Remove sensitive data that isn't necessary for audit validation
6. **Completeness**: Cover entire audit period, all quarters, no gaps

CONSTRAINTS:
- Every evidence item listed must actually exist and be accessible
- Sanitization must be completed BEFORE package assembly (don't just note "will redact")
- File references must be accurate (correct filenames, locations)
- If evidence is weak for a period, note it honestly: "[Q3 review delayed 2 weeks due to X, but completed before Q4]"
```

**🏢 Enterprise Tool Additions:**
- Name specific tools (Okta, ServiceNow, Workday, etc.)
- Include actual file paths and document repositories
- Reference specific ticket numbers or report IDs
- Use actual date ranges for audit period
- Include specific metrics and coverage percentages

**🌐 Consumer Tool Restrictions:**
- Use generic tool categories (IAM system, ticketing platform)
- Abstract file locations to general descriptions
- Don't include specific ticket or record identifiers
- Use relative date descriptions
- Use percentage ranges rather than specific metrics

**Verification Checklist:**
- [ ] Every evidence item listed is actually available
- [ ] All sensitive information has been sanitized appropriately
- [ ] Coverage spans entire audit period with no gaps
- [ ] Evidence demonstrates both implementation AND effectiveness
- [ ] File naming and organization are consistent throughout
- [ ] Package includes process + execution + effectiveness + oversight
- [ ] Cross-references between related evidence are accurate

**Iteration Guidance:**
- If organization seems illogical: Explain auditor's typical review sequence
- If evidence seems insufficient: Identify what's missing: "We need evidence of [X] to demonstrate [control aspect]"
- If too complex: Request simpler structure: "Organize by time period only" or "Group by evidence type only"
- If sanitization unclear: Specify what must be removed: "Remove all [employee names/IPs/system versions]"

---
