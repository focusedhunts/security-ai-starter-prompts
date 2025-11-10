# Offensive Security: Reporting and Documentation Starter Prompt

## Purpose
This starter prompt helps offensive security professionals transform technical findings from penetration tests, red team engagements, and security assessments into comprehensive, actionable reports. It addresses both technical documentation for remediation teams and executive communication for leadership audiences.

**Important**: This is a STARTER prompt requiring customization for your specific engagement, client context, and findings. It demonstrates the four principles of effective prompting but must be adapted to your situation.

---

## Core Prompt Framework

### Context Section (Customize These Details)

**Engagement Context:**
```
I conducted an authorized [ENGAGEMENT TYPE: external penetration test / internal security assessment / red team operation / assumed breach exercise] for [CLIENT TYPE: financial services organization / healthcare provider / technology company / government agency] over [TIMEFRAME]. 

The engagement scope included [SCOPE DESCRIPTION: external-facing infrastructure / internal network and applications / cloud environment / physical security testing].

Authorization: [AUTHORIZATION DETAILS: signed SOW dated X / bug bounty program / internal security assessment]
```

**Audience and Purpose:**
```
I need to create a [REPORT TYPE: comprehensive penetration test report / red team engagement report / security assessment] for:

Primary Audience: [SPECIFY: technical remediation team / CISO and security leadership / executive team and board / mixed technical and business audience]

Technical Level: [SPECIFY: deep technical detail for security engineers / moderate technical detail with business context / high-level business risk focus / multiple sections for different audiences]

Report Purpose: [SPECIFY: drive remediation prioritization / demonstrate security posture / satisfy compliance requirements / inform security strategy]
```

**Findings Overview (Provide High-Level Summary):**
```
The engagement identified [NUMBER] findings across [CATEGORIES: web application vulnerabilities / network security gaps / access control issues / social engineering susceptibilities / physical security weaknesses].

Key findings include:
- [CRITICAL FINDING 1 - general description without sensitive details]
- [HIGH FINDING 1 - general description]
- [NOTEWORTHY PATTERN - general description]

Attack chain summary: [BRIEF DESCRIPTION of how findings could be chained, e.g., "Initial access through exposed service led to credential compromise, enabling lateral movement and privilege escalation"]
```

---

## Specificity Requirements

### Report Structure
```
Generate the report using the following structure:

1. EXECUTIVE SUMMARY (1-2 pages)
   - Overall security posture assessment
   - Key findings in business risk language
   - Risk summary by category
   - High-level remediation roadmap

2. TECHNICAL FINDINGS (Detailed)
   For each finding include:
   - Finding title and unique identifier
   - Severity rating: [YOUR METHODOLOGY: CVSS / OWASP / Custom scale]
   - Affected systems/applications
   - Technical description
   - Reproduction steps
   - Evidence references (screenshots, logs, etc.)
   - Business impact
   - Remediation recommendations
   - References to standards/frameworks

3. ATTACK NARRATIVES
   - End-to-end attack chains demonstrated
   - Progression through kill chain stages
   - Decision points and defensive control gaps
   - Realistic adversary perspective

4. METHODOLOGY AND SCOPE
   - Testing approach and techniques used
   - Tools and frameworks employed
   - Scope boundaries and limitations
   - Timeline and effort summary

5. REMEDIATION ROADMAP
   - Prioritized remediation plan
   - Quick wins vs. strategic improvements
   - Resource requirements
   - Risk reduction timeline

6. DEFENSIVE RECOMMENDATIONS
   - Detection and monitoring improvements
   - Architecture changes
   - Process enhancements
   - Training recommendations
```

### Severity Rating Guidance
```
Apply the following severity framework [CUSTOMIZE TO YOUR METHODOLOGY]:

CRITICAL: [YOUR DEFINITION - e.g., "Direct path to domain admin / data exfiltration / system compromise with no user interaction required"]

HIGH: [YOUR DEFINITION - e.g., "Significant security control bypass / sensitive data exposure / privilege escalation requiring minimal interaction"]

MEDIUM: [YOUR DEFINITION - e.g., "Security weakness requiring chaining with other vulnerabilities / information disclosure / denial of service"]

LOW: [YOUR DEFINITION - e.g., "Security configuration improvements / defense-in-depth recommendations / informational findings"]

INFORMATIONAL: [YOUR DEFINITION - e.g., "Observations that don't represent immediate risk but warrant documentation"]
```

### Evidence Handling
```
For each finding, I will reference evidence as:
- Screenshot [NUMBER]: [BRIEF DESCRIPTION]
- Log excerpt [NUMBER]: [BRIEF DESCRIPTION]  
- Network capture [NUMBER]: [BRIEF DESCRIPTION]
- Command output [NUMBER]: [BRIEF DESCRIPTION]

[IMPORTANT - DATA SANITIZATION]
When drafting the report:
- Replace actual IP addresses with placeholders: [TARGET-IP], [INTERNAL-IP-1]
- Replace actual hostnames with descriptors: [WEB-SERVER], [DC-PRIMARY]
- Replace actual usernames with roles: [DOMAIN-ADMIN], [SERVICE-ACCOUNT]
- Replace actual credentials with indicators: [DISCOVERED-PASSWORD], [COMPROMISED-KEY]
- Generalize system versions unless specifically relevant: "outdated web server" vs "Apache 2.4.10"
- Abstract company-specific details: [CLIENT] instead of company name

I will provide specific evidence details separately for inclusion in the final report appendix.
```

---

## Structure Requirements

### Executive Summary Generation
```
For the executive summary section:

1. Write opening paragraph that provides overall security posture assessment without technical jargon
2. Translate technical findings into business risk language:
   - Instead of "SQL injection vulnerability": "Critical weakness allowing unauthorized access to customer database"
   - Instead of "Missing patch CVE-2024-XXXX": "Known vulnerability exposing sensitive systems to compromise"
   - Instead of "Weak authentication controls": "Inadequate safeguards protecting administrative access"

3. Present risk summary organized by:
   - Business impact (data exposure / system availability / financial loss / regulatory compliance)
   - Attack feasibility (external attacker / insider threat / supply chain)
   - Remediation complexity (configuration change / architecture redesign / process improvement)

4. Provide high-level remediation roadmap with three phases:
   - Immediate (0-30 days): Critical findings requiring urgent attention
   - Near-term (30-90 days): High-priority improvements
   - Strategic (90+ days): Architecture and process enhancements

5. Include metrics that matter to executives:
   - Time to compromise from external perspective
   - Number of critical systems affected
   - Comparison to industry baseline
   - Risk reduction if recommendations implemented
```

### Technical Findings Documentation
```
For each technical finding, structure as follows:

FINDING TITLE: [Descriptive, searchable title]
FINDING ID: [Unique identifier for tracking]
SEVERITY: [Critical/High/Medium/Low/Informational]

AFFECTED SYSTEMS:
- [System/application identifier]
- [Scope of impact]

TECHNICAL DESCRIPTION:
[2-3 paragraphs explaining the vulnerability or weakness, including:
- What the vulnerability is
- Why it exists (root cause)
- Technical conditions required for exploitation]

REPRODUCTION STEPS:
1. [Step-by-step instructions that technical team can follow]
2. [Include specific commands, requests, or actions taken]
3. [Clear enough for validation, sanitized enough for security]

EVIDENCE:
- Reference to Screenshot [X]
- Reference to Log excerpt [Y]
- Reference to relevant appendix section

BUSINESS IMPACT:
[Translate technical impact to business consequences:
- Data confidentiality, integrity, or availability impact
- System availability concerns
- Compliance implications
- Potential for lateral movement or escalation]

REMEDIATION:
Short-term fix: [Immediate action to reduce risk]
Long-term solution: [Proper remediation addressing root cause]
Validation: [How to confirm fix is effective]

REFERENCES:
- [Relevant CVE, CWE, or OWASP reference]
- [Vendor security advisory if applicable]
- [Framework control mapping: NIST CSF, MITRE ATT&CK, etc.]
```

### Attack Narrative Construction
```
For attack chain narratives:

1. Set the scene with realistic adversary perspective:
   "An external attacker with no prior knowledge of the organization could achieve the following compromise chain..."

2. Structure by attack phases:
   - RECONNAISSANCE: What information was gathered and how
   - INITIAL ACCESS: How entry was achieved
   - EXECUTION: What commands or payloads were run
   - PERSISTENCE: How continued access was maintained
   - PRIVILEGE ESCALATION: How higher privileges were obtained
   - LATERAL MOVEMENT: How attacker moved through environment
   - COLLECTION: What data or credentials were accessed
   - IMPACT: What ultimate objectives were achieved

3. For each phase, explain:
   - What was done (actions taken)
   - How it was done (techniques used)
   - Why it was possible (security control gaps)
   - What could have prevented it (defensive recommendations)

4. Use evidence references throughout to support narrative

5. Conclude with "attacker's perspective" summary of how easy or difficult the compromise was
```

### Remediation Roadmap
```
Organize remediation recommendations as:

IMMEDIATE ACTIONS (0-30 days) - Critical Risk Reduction
[List findings requiring urgent attention with:
- Finding ID and title
- Why urgent (business impact)
- Recommended action
- Estimated effort
- Dependencies]

NEAR-TERM IMPROVEMENTS (30-90 days) - Significant Risk Reduction  
[List high-priority findings with:
- Finding ID and title
- Risk reduction value
- Recommended action
- Resource requirements
- Quick wins vs. complex changes]

STRATEGIC ENHANCEMENTS (90+ days) - Long-term Posture Improvement
[List architecture and process improvements with:
- Category (architecture / detection / process)
- Current state gap
- Recommended future state
- Benefits beyond addressing specific findings
- Implementation complexity]

For each remediation item, consider:
- Risk reduction value (HIGH/MEDIUM/LOW)
- Implementation difficulty (EASY/MODERATE/HARD)
- Dependencies on other remediations
- Suggested ownership (team/role responsible)
```

### Defensive Recommendations
```
Provide recommendations across multiple defensive layers:

DETECTION AND MONITORING:
[Based on attack techniques demonstrated during engagement:
- Specific log sources to enable
- SIEM rules or detection logic to implement
- Alerting thresholds to configure
- Response playbooks to develop
Reference specific MITRE ATT&CK techniques where applicable]

ARCHITECTURE IMPROVEMENTS:
[Systemic issues identified:
- Network segmentation opportunities
- Zero trust architecture considerations
- Defense-in-depth gaps
- Security control placement]

PROCESS ENHANCEMENTS:
[Operational security improvements:
- Patch management process
- Vulnerability management workflow
- Change control procedures
- Security review checkpoints
- Incident response plan updates]

AWARENESS AND TRAINING:
[Human element observations:
- Security awareness gaps demonstrated
- Technical training opportunities
- Tabletop exercise scenarios based on engagement
- Phishing simulation recommendations if applicable]
```

---

## Iteration and Refinement

### Initial Draft Generation
```
Generate the initial report draft following the structure above. Focus on:
1. Clear, professional language appropriate for specified audience
2. Consistent formatting and organization
3. Logical flow from high-level to detailed technical content
4. Business impact emphasis without losing technical accuracy
```

### Refinement Prompts (Use After Initial Draft)

**For Executive Summary Refinement:**
```
Review the executive summary and:
1. Remove any remaining technical jargon that business audience wouldn't understand
2. Strengthen business impact statements with specific consequences
3. Ensure remediation roadmap has clear priority rationale
4. Add comparison to industry baseline if available: [PROVIDE CONTEXT]
```

**For Technical Findings Refinement:**
```
Review the technical findings section and:
1. Verify reproduction steps are clear enough for technical team to validate
2. Confirm evidence references are consistently formatted
3. Ensure remediation guidance is actionable and specific
4. Check that severity ratings follow the defined methodology consistently
```

**For Tone and Audience Adjustment:**
```
The report needs adjustment for [NEW AUDIENCE or PURPOSE]:
- [Specify change: more/less technical detail, different focus area, compliance angle, etc.]
- Maintain factual accuracy while adjusting presentation
- Preserve key findings and recommendations
```

**For Compliance Mapping:**
```
Add compliance framework mapping to findings:
- Framework: [SPECIFY: NIST CSF / ISO 27001 / PCI DSS / SOC 2]
- For each finding, identify which controls or requirements are affected
- Include compliance impact in business risk assessment
```

---

## Quality Verification Checklist

Before finalizing the report, verify:

**Accuracy:**
- [ ] All technical details reflect actual testing observations
- [ ] Severity ratings align with defined methodology and business context
- [ ] Reproduction steps have been validated
- [ ] Evidence references are correct and complete

**Completeness:**
- [ ] All significant findings are documented
- [ ] Attack chains are fully explained
- [ ] Remediation guidance addresses both symptoms and root causes
- [ ] Scope and limitations are clearly stated

**Clarity:**
- [ ] Executive summary is understandable without technical background
- [ ] Technical sections provide sufficient detail for remediation
- [ ] Business impact is clearly articulated for each finding
- [ ] Recommendations are specific and actionable

**Security:**
- [ ] Sensitive details are appropriately sanitized in AI-generated sections
- [ ] Client confidential information is protected
- [ ] Exploitation details won't enable malicious use by unauthorized parties
- [ ] Evidence handling follows proper information security practices

**Professionalism:**
- [ ] Tone is constructive and professional, not accusatory
- [ ] Language is precise and avoids hyperbole
- [ ] Formatting is consistent throughout
- [ ] Document is suitable for contractual deliverable or formal submission

---

## Important Reminders

### Data Handling for AI Tools

**Enterprise AI Tools (Preferred for Report Generation):**
- Use tools with data processing agreements
- Suitable for sanitized findings and general recommendations
- Still require sanitization of client-specific details
- Verify tool's data retention and usage policies

**Consumer AI Tools (Limited Use Cases):**
- Only for general report structure and formatting guidance
- Never include client names, actual findings, or sensitive details
- Use only for learning report writing techniques
- Assume prompts and outputs may be retained

**Never Include in Any AI Tool:**
- Actual credentials discovered during testing
- Client employee names or personal information
- Specific IP addresses or network topology
- Detailed system configurations
- Proprietary business information learned during engagement

### Verification Requirements

**Before Using AI-Generated Report Content:**
1. Verify all technical facts against your actual testing notes
2. Confirm reproduction steps work as described
3. Validate that severity ratings match your methodology and business context
4. Review business impact statements for accuracy
5. Ensure recommendations are appropriate for client's environment

**Critical Review Areas:**
- AI may suggest generic remediation that doesn't fit client's architecture
- AI may miss nuances of specific findings that change severity
- AI may generate plausible-sounding technical details that aren't quite right
- AI cannot assess political or organizational factors affecting remediation feasibility

### Professional Boundaries

This prompt assists with report **structure and articulation**, not with:
- Determining what constitutes a vulnerability (requires security expertise)
- Assessing appropriate severity (requires business context and threat modeling)
- Creating recommendations (requires understanding of client constraints)
- Making decisions about disclosure (requires professional judgment)

**You remain responsible for:**
- Factual accuracy of all content
- Professional judgment on severity and priority
- Appropriateness of recommendations for client context
- Compliance with engagement scope and authorization
- Protection of client confidential information

---

## Example Usage Workflow

1. **Preparation:**
   - Organize your testing notes and evidence
   - Sanitize any sensitive details you'll reference
   - Review engagement scope and objectives
   - Identify primary audience and report purpose

2. **Initial Generation:**
   - Customize the Context Section with your engagement details
   - Provide high-level findings summary (sanitized)
   - Specify report structure requirements
   - Generate initial draft

3. **Iterative Refinement:**
   - Review draft against your actual findings
   - Use refinement prompts to adjust tone, detail level, or focus
   - Add specific evidence details you held back from initial prompt
   - Verify technical accuracy of all AI-generated content

4. **Final Assembly:**
   - Integrate AI-generated narrative with your evidence
   - Add actual system details, screenshots, and logs
   - Review against quality verification checklist
   - Apply final formatting and branding

5. **Quality Assurance:**
   - Have peer review technical accuracy
   - Verify all sensitive details are appropriately handled
   - Confirm report meets engagement deliverable requirements
   - Check that recommendations are actionable and specific

---

## Customization Notes

**Adapt This Prompt For:**
- Different engagement types (adjust methodology section)
- Various report formats (modify structure section)
- Specific compliance requirements (add framework mapping)
- Different audience technical levels (adjust detail and terminology)
- Industry-specific contexts (modify business impact language)
- Client reporting preferences (customize formatting and organization)

**Common Customizations:**
- Adding client-specific terminology and acronyms
- Incorporating organization's severity rating methodology
- Aligning with specific reporting templates or standards
- Including required compliance or contractual language
- Adjusting technical depth based on audience expertise

Remember: This starter prompt provides a framework following the four principles (context, specificity, structure, iteration). Your professional expertise, testing observations, and client knowledge transform this framework into a valuable security deliverable.

---

## Additional Resources

**Companion Repository:**
https://github.com/focusedhunts/security-ai-starter-prompts

Contains additional examples, customization guidance, and community contributions for offensive security reporting.

**Related Starter Prompts:**
- Reconnaissance and Intelligence Gathering
- Attack Path Identification and Planning
- Initial Access Operations
- Exploitation and Post-Exploitation

Each can provide inputs that feed into comprehensive reporting.
