## 1. Control Statement Development

**Task:** Generate audit-ready control statement for certification/compliance framework
**Advanced Techniques:** Persona-based prompting, constraint-based output, structured format specification
**Principles Applied:** Context (role + implementation), Specificity (exact control), Structure (consistent format), Iteration (refinement guidance)

```markdown
You are an experienced compliance analyst preparing control statements for [FRAMEWORK_NAME] certification audit. Your audience is external auditors who need to verify control implementation and effectiveness.

FRAMEWORK CONTEXT:
- Framework: [FRAMEWORK_NAME and VERSION] (e.g., ISO 27001:2022, SOC 2 2017 TSC, NIST CSF 2.0)
- Specific Control: [CONTROL_ID and FULL_NAME] (e.g., A.9.2.1 User registration and de-registration)
- Audit Type: [INITIAL_CERTIFICATION / SURVEILLANCE / RECERTIFICATION]
- Auditor Focus Areas: [IMPLEMENTATION_EVIDENCE / EFFECTIVENESS_METRICS / CONTINUOUS_IMPROVEMENT]

IMPLEMENTATION CONTEXT:
Think step-by-step about our control implementation:
1. Technology Layer: [SANITIZED_TOOL_DESCRIPTION]
   🏢 Enterprise: "We use [Okta/Azure AD/specific IAM platform] with automated provisioning"
   🌐 Consumer: "We use an enterprise identity management platform with automated provisioning"

2. Process Layer: [WORKFLOW_DESCRIPTION]
   Example: "New accounts require [manager/security/dual] approval through [ticketing system]"

3. Integration Layer: [SYSTEM_CONNECTIONS]
   🏢 Enterprise: "HR system [Workday/BambooHR] triggers provisioning via API integration"
   🌐 Consumer: "HR system triggers provisioning through documented integration points"

4. Validation Layer: [REVIEW_MECHANISMS]
   Example: "[Quarterly/Monthly] access reviews by [department managers/security team]"

5. Enforcement Layer: [TERMINATION_HANDLING]
   Example: "Terminated employee access revoked within [X hours/same day] of HR notification"

ORGANIZATIONAL CONTEXT:
- Company Size: [NUMBER] employees
- Industry: [SECTOR] with [REGULATORY_REQUIREMENTS]
- User Base: [TECHNICAL/BUSINESS/MIXED] workforce
- Operating Model: [REMOTE/HYBRID/ON-SITE]

CONSTRAINTS:
- You must only use information I've provided above; do not assume implementation details
- Do not include aspirational controls we haven't implemented
- Keep technical detail appropriate for auditor validation without exposing security vulnerabilities

OUTPUT REQUIREMENTS:
Generate a control statement using this exact structure:

**1. Control Objective** (1 sentence)
State what security outcome this control achieves

**2. Implementation Description** (3-4 sentences)
Describe HOW we implement this control covering:
- People: Who performs what actions
- Process: What workflows are followed  
- Technology: What systems enforce the control

**3. Evidence Available for Audit** (bulleted list)
- [Type of evidence 1]: [Specific artifact]
- [Type of evidence 2]: [Specific artifact]
- [Type of evidence 3]: [Specific artifact]

**4. Control Effectiveness Validation** (2 sentences)
Explain how we verify this control works as intended (metrics, testing, reviews)

**5. Responsible Party** (role, not individual name)
[JOB_TITLE or TEAM] has ongoing responsibility for control operation

TONE: Professional, precise, verifiable - suitable for external audit submission.
```

**🏢 Enterprise Tool Additions:**
- Include specific tool names (they're already in your audit scope)
- Reference exact approval workflows and system names
- Specify your actual SLAs and review frequencies
- Mention specific integration points

**🌐 Consumer Tool Restrictions:**
- Use generic technology categories only ("enterprise IAM", "ticketing platform")
- Abstract approval workflows to general descriptions
- Don't specify exact SLAs that reveal security posture
- Remove any system architecture details

**Verification Checklist:**
- [ ] Every claim is factually accurate against actual implementation
- [ ] Evidence listed actually exists and is accessible for audit
- [ ] Control description matches documented procedures
- [ ] No sensitive configuration details exposed
- [ ] Approved by control owner before audit submission

**Iteration Guidance:**
- If output is too technical: Add "Explain for auditors with [business/limited technical] background"
- If output is too generic: Provide more specific implementation details (sanitized appropriately)
- If wrong tone: Specify "Must satisfy [internal/external/regulatory] auditors"

---
