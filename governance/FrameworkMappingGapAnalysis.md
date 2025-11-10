## 3. Framework Mapping and Gap Analysis

**Task:** Map controls across multiple compliance frameworks and identify implementation gaps

**Advanced Techniques:** Structured output (table format), comparative analysis, prioritization logic

**Principles Applied:** Structure (comparison framework), Specificity (mapping granularity), Context (organizational implementation)

```markdown
You are a compliance analyst performing cross-framework control mapping to identify coverage and gaps for multi-framework certification.

MAPPING OBJECTIVE:
Map our implemented security controls across [NUMBER] frameworks to:
1. Identify where single controls satisfy multiple framework requirements (efficiency)
2. Discover gaps where framework requirements aren't met (risk)
3. Prioritize gap remediation based on compliance obligations and implementation complexity

FRAMEWORKS IN SCOPE:
List each framework with exact version:
1. [FRAMEWORK_NAME VERSION] - [Certification status: Current/Planned/Considering]
2. [FRAMEWORK_NAME VERSION] - [Certification status]
3. [FRAMEWORK_NAME VERSION] - [Certification status]

Example:
1. NIST Cybersecurity Framework 2.0 - Current (using for internal program)
2. ISO 27001:2022 - Planned (seeking certification Q2 2025)
3. SOC 2 (2017 TSC) - Current (Type II certified, annual audit)

FOCUS DOMAIN:
Security Domain: [DOMAIN_NAME] (e.g., Access Control, Data Protection, Incident Response)

Specific framework sections to map:
- [FRAMEWORK_1]: [Section/Category] (e.g., NIST CSF: PR.AC - Identity Management)
- [FRAMEWORK_2]: [Section/Category] (e.g., ISO 27001: Annex A.9 - Access Control)
- [FRAMEWORK_3]: [Section/Category] (e.g., SOC 2: CC6 - Logical and Physical Access)

CURRENT IMPLEMENTATION STATE:
For this domain, we have documented controls covering:

🏢 Enterprise: Be specific about your controls:
- [Control 1]: [Specific implementation] (e.g., "Automated user provisioning via Okta integrated with Workday HR system")
- [Control 2]: [Specific implementation] (e.g., "MFA enforcement using Duo for all users, hardware tokens for privileged access")
- [Control 3]: [Specific implementation] (e.g., "Quarterly access reviews in ServiceNow with manager attestation")

🌐 Consumer: Use generic descriptions:
- [Control 1]: [Generic implementation] (e.g., "Automated user provisioning via IAM system integrated with HR platform")
- [Control 2]: [Generic implementation] (e.g., "Multi-factor authentication enforced for all user types")
- [Control 3]: [Generic implementation] (e.g., "Periodic access reviews with management validation")

ORGANIZATIONAL CONSTRAINTS (for gap prioritization):
- Compliance Deadlines: [FRAMEWORK]: [DATE] certification required
- Resource Limitations: [TEAM_SIZE], [BUDGET_CONSTRAINTS]
- Technical Debt: [SPECIFIC_LIMITATIONS]
  🏢 Enterprise: "Legacy mainframe applications that cannot support SSO"
  🌐 Consumer: "Legacy systems with limited integration capabilities"

---

MAPPING TASK:

Think through this mapping systematically:

STEP 1: For each control we've implemented (listed above), identify which framework requirements it satisfies.

STEP 2: For each framework requirement in the focus domain, assess:
- Full Coverage: Our control completely satisfies this requirement
- Partial Coverage: Our control partially satisfies, but gaps exist
- No Coverage: We have no control addressing this requirement

STEP 3: For Partial or No Coverage, specify:
- What specifically is missing?
- Why is it missing (technical limitation, resource constraint, not yet implemented)?
- What would full implementation require?

OUTPUT FORMAT:

Create a comprehensive mapping table with these columns:

| Our Control (Implemented) | [Framework 1] Control(s) | [Framework 2] Control(s) | [Framework 3] Control(s) | Coverage Status | Gap Details | Implementation Effort | Priority |

For controls we DON'T have (gaps identified):

| Missing Control (Gap) | [Framework 1] Requirement | [Framework 2] Requirement | [Framework 3] Requirement | Business Impact | Implementation Complexity | Recommended Priority | Dependencies |

---

AFTER THE TABLES, provide:

**COVERAGE ANALYSIS SUMMARY:**
1. Controls satisfying multiple frameworks (evidence collection efficiency opportunities)
2. Framework-specific requirements with no overlap (must implement separately)
3. Total gap count by framework
4. Percentage coverage by framework

**GAP PRIORITIZATION RATIONALE:**
For each identified gap, explain priority rating based on:
- Compliance obligation severity (regulatory requirement vs. best practice)
- Risk if not implemented (what could go wrong)
- Implementation complexity (resource, time, technical challenges)
- Dependencies (what must be done first)

Use this priority scale:
- CRITICAL: Mandatory for upcoming certification, high risk, must implement immediately
- HIGH: Required for compliance, moderate risk, implement within [X timeframe]
- MEDIUM: Best practice or future requirement, manageable risk, plan for implementation
- LOW: Nice-to-have, low risk, implement as resources allow

**REMEDIATION ROADMAP:**
Sequence gap remediation logically:
- Q1 [YEAR]: [CRITICAL gaps to address]
- Q2 [YEAR]: [HIGH priority gaps]
- Q3-Q4 [YEAR]: [MEDIUM priority gaps]

CONSTRAINTS:
- Base priority only on information provided (don't assume organizational context)
- If implementation details are unclear, note "[Requires stakeholder input on X]"
- For technical complexity assessments, consider typical enterprise implementation challenges
```

**🏢 Enterprise Tool Additions:**
- Include specific tool names and versions in control descriptions
- Reference actual certification timelines and auditor requirements
- Specify real technical limitations and architecture constraints
- Name actual frameworks you're certified against or pursuing

**🌐 Consumer Tool Restrictions:**
- Use technology categories, not specific vendor products
- Keep timelines generic ("upcoming certification cycle")
- Abstract technical limitations to general categories
- Don't specify which frameworks your organization uses

**Verification Checklist:**
- [ ] Every "Implemented" control listed actually exists and is documented
- [ ] Framework control mappings are accurate to specified versions
- [ ] Gap analysis reflects honest assessment (no aspirational coverage claims)
- [ ] Priority ratings align with actual organizational compliance obligations
- [ ] Remediation roadmap is realistic given stated resource constraints

**Iteration Guidance:**
- If mappings seem wrong: Verify framework version numbers are correct
- If gaps seem incomplete: Add more detail about current implementation state
- If priorities don't align with your needs: Provide more context about business drivers
- If table format is hard to read: Request alternative format (nested lists, separate tables per framework)

---
