## 2. Policy Writing with Requirement Analysis

**Task:** Develop policy section based on multi-framework compliance requirements

**Advanced Techniques:** Phased analysis, chain-of-thought reasoning, negative prompting

**Principles Applied:** Structure (phased approach), Context (regulatory environment), Specificity (requirement extraction)

```markdown
You are a policy development specialist analyzing regulatory requirements to draft compliant security policy provisions. Use systematic analysis before drafting.

POLICY DEVELOPMENT TASK:
Policy Section: [POLICY_DOMAIN] (e.g., Data Classification, Access Control, Incident Response)
Target Policy Document: [DOCUMENT_NAME]

ORGANIZATIONAL CONTEXT:
- Industry: [SECTOR] (e.g., Healthcare, Financial Services, Technology)
- Company Size: [EMPLOYEES/REVENUE_RANGE]
- Regulatory Environment: [PRIMARY_REGULATIONS]
  🏢 Enterprise: "Subject to HIPAA, CCPA, SOC 2 Type II, considering ISO 27001 certification"
  🌐 Consumer: "Subject to [industry standard frameworks], considering certification"

- Data Handled: [TYPES_OF_SENSITIVE_DATA]
  🏢 Enterprise: "Patient health information (PHI), payment card data (PCI), employee PII"
  🌐 Consumer: "Regulated sensitive data including personal information"

- Current Security Maturity: [NASCENT/DEVELOPING/MATURE]

APPLICABLE FRAMEWORKS:
List frameworks that apply to this policy area:
1. [FRAMEWORK_1 with VERSION] - [Specific controls/sections relevant]
2. [FRAMEWORK_2 with VERSION] - [Specific controls/sections relevant]
3. [FRAMEWORK_3 with VERSION] - [Specific controls/sections relevant]

Example:
1. HIPAA Security Rule - §164.308(a)(3) Workforce Security
2. SOC 2 (2017) - CC6.1 Logical Access Controls
3. ISO 27001:2022 - A.9 Access Control

POLICY AUDIENCE:
- Primary: [ALL_EMPLOYEES / TECHNICAL_STAFF / SPECIFIC_ROLES]
- Technical Literacy: [HIGH/MEDIUM/LOW]
- Decision-Makers Who Approve: [EXECUTIVE_TEAM/BOARD/COMPLIANCE_COMMITTEE]

IMPLEMENTATION CONSTRAINTS:
🏢 Enterprise: Be specific about your actual constraints:
- Technical: [Specific limitations like "Legacy applications that cannot support MFA"]
- Operational: [Resource constraints like "2-person security team supporting 500 users"]
- Business: [Specific needs like "24/7 customer support requiring flexible access"]

🌐 Consumer: Keep constraints generic:
- Technical: [General limitations like "Mixed environment with varying technical capabilities"]
- Operational: [General constraints like "Resource-constrained security function"]
- Business: [General needs like "Balance security with operational efficiency"]

---

PHASE 1: REQUIREMENT EXTRACTION
Before drafting policy language, analyze each framework and extract:

For each framework listed above, identify:
1. What specific requirements does this framework mandate for [POLICY_DOMAIN]?
2. What controls are required vs. recommended?
3. What evidence or documentation does this framework expect?
4. What language or terminology does this framework use that we should mirror?

Think through this systematically for each framework before moving to Phase 2.

---

PHASE 2: CONFLICT AND GAP ANALYSIS
Based on your Phase 1 analysis:

1. Identify requirement conflicts:
   - Where do frameworks require different approaches?
   - How can we satisfy both/all requirements?

2. Identify coverage gaps:
   - What does Framework A require that Framework B doesn't mention?
   - Are there areas where multiple frameworks overlap?

3. Distinguish required vs. best practice:
   - What must be in policy (mandatory)?
   - What can be in supporting procedures (implementation detail)?

Think through these conflicts before synthesizing requirements.

---

PHASE 3: POLICY DRAFTING
Based on your analysis from Phases 1 and 2, draft the [POLICY_DOMAIN] section of our policy.

POLICY STRUCTURE REQUIRED:
**[Policy Section Title]**

**1. Purpose Statement** (2-3 sentences)
Explain why this policy exists - what security outcome it achieves and what risks it addresses

**2. Scope** (1-2 sentences)
Define what/who this policy applies to - be specific about coverage

**3. Policy Requirements** (5-8 numbered provisions)
Each requirement must:
- Use "must" for mandatory requirements, "should" for recommendations
- Be clear enough for non-technical employees to understand their obligations
- Be specific enough to be auditable and enforceable
- Map to at least one framework requirement (note this in your analysis)

Format: "[Role/System] must [specific action] [under what conditions]"
Example: "All users must authenticate using multi-factor authentication when accessing systems containing [data classification]"

**4. Roles and Responsibilities** (bulleted list)
Define who is responsible for:
- Policy implementation
- Compliance monitoring
- Exception approvals
- Periodic review

**5. Exceptions Process** (2-3 sentences)
How can someone request an exception, who approves, what documentation is required

CRITICAL CONSTRAINTS:
- Do NOT include implementation details (those go in procedures, not policy)
- Do NOT assume controls we haven't implemented
- Do NOT use security jargon without defining it for non-technical audience
- Do NOT make policy so restrictive it's unenforceable

LENGTH: 2-3 pages maximum (board needs to review and approve)

TONE: Authoritative but accessible - this sets organizational requirements that all employees must follow
```

**🏢 Enterprise Tool Additions:**
- Reference your specific regulatory obligations (HIPAA, PCI-DSS, GDPR, etc.)
- Name your actual data types and classifications
- Specify your real implementation constraints
- Include your actual approval chain

**🌐 Consumer Tool Restrictions:**
- Use generic regulatory categories ("healthcare regulations", "financial compliance")
- Abstract data types to general categories
- Keep constraints non-specific
- Reference generic organizational structures

**Verification Checklist:**
- [ ] Every policy requirement reflects actual capability (not aspirational)
- [ ] All framework references are accurate to specified versions
- [ ] Language is appropriate for target audience literacy level
- [ ] Policy is enforceable with available resources
- [ ] Legal counsel has reviewed regulatory interpretation (if applicable)
- [ ] Appropriate stakeholders have approved

**Iteration Guidance:**
- If too technical: Add "Simplify language for [specific audience with X background]"
- If requirements unclear: Add examples: "For instance, [specific scenario]"
- If conflicts unresolved: Provide more context about which framework takes precedence in your organization
- If too prescriptive: Specify "Focus on 'what' not 'how' - implementation goes in procedures"

---
