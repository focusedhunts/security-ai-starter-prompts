## 7. Audit Response Drafting

**Task:** Draft comprehensive response to auditor questions about control implementation

**Advanced Techniques:** Question decomposition, structured answering, constraint-based verification

**Principles Applied:** Specificity (exact question), Context (implementation details), Structure (clear answer format)

```markdown
You are a compliance analyst drafting a formal response to an auditor question during [FRAMEWORK] audit. Your response will become part of the official audit record and must be factually accurate, complete, and verifiable.

AUDITOR QUESTION (exact wording):
[Paste the complete auditor question exactly as asked]

Example: "Please describe your process for managing security patches and system updates across your infrastructure. Specifically address: (1) How you identify required patches, (2) Your risk assessment and prioritization methodology, (3) Testing procedures before production deployment, (4) Timelines for critical vs. non-critical patches, (5) How you handle patches requiring system downtime."

AUDIT CONTEXT:
- Framework: [FRAMEWORK_NAME VERSION]
- Control(s) Being Assessed: [CONTROL_IDS]
- Audit Phase: [PLANNING / FIELDWORK / FOLLOW-UP]
- Auditor Type: [EXTERNAL_CERTIFICATION / INTERNAL / REGULATORY]

YOUR IMPLEMENTATION:
Provide details about how you actually implement this control/process:

🏢 Enterprise: Be specific about your implementation:
- Tools: [Specific vulnerability scanners, patch management systems]
- Process: [Detailed workflow with roles and timelines]
- Integration: [How systems connect, what triggers actions]
- Exception Handling: [What happens when normal process can't be followed]
- Metrics: [How you measure effectiveness]

Example: "We use Tenable for weekly vulnerability scanning. Patches identified via Tenable + vendor security mailing lists. Risk prioritization: CVSS score + asset criticality matrix + exploitability assessment. Testing in staging environment (mirrors production). Critical patches (CVSS 9.0+, known exploitation): 72-hour emergency process with CAB approval. Standard patches: monthly maintenance window (2nd Sunday). Downtime requires 48-hour customer notification per SLA."

🌐 Consumer: Keep implementation generic:
- Tools: [Tool categories without vendor names]
- Process: [General workflow descriptions]
- Integration: [High-level automation descriptions]
- Exception Handling: [General governance approach]
- Metrics: [Types of measurements without specifics]

Example: "Automated vulnerability scanning conducted regularly. Patches identified through scanning tools and vendor advisories. Risk prioritization based on severity scoring and asset classification. Testing performed in non-production environment. Critical patches follow expedited approval process. Standard patches deployed during scheduled maintenance. Downtime managed per customer communication requirements."

DOCUMENTED PROCEDURES:
- Procedure Name: [Reference document name and version]
- Procedure Location: [Where auditor could find this]
  🏢 Enterprise: "Patch Management Procedure v3.2 (SharePoint > Security Policies > Procedures)"
  🌐 Consumer: "Patch management procedure (current version in policy repository)"

EVIDENCE AVAILABLE:
What evidence can you provide to support your response?
- [Evidence type 1]: [Specific artifact]
- [Evidence type 2]: [Specific artifact]
- [Evidence type 3]: [Specific artifact]

Example: "Tenable scan reports (weekly), CAB meeting minutes, Patch deployment tickets from ServiceNow, Customer notification emails, Exception approval records"

---

RESPONSE DRAFTING TASK:

Analyze the auditor question carefully:
1. Identify each specific sub-question or requirement
2. Map which part of your implementation addresses each
3. Structure response to address each point explicitly
4. Include evidence references for verifiability

Think through: "What is the auditor really trying to verify here?"
- Process existence? (Do you have one?)
- Process execution? (Do you follow it?)
- Process effectiveness? (Does it work?)
- Oversight? (Is management engaged?)
- Consistency? (Do you do this reliably?)

OUTPUT STRUCTURE:

**Auditor Question:** [Repeat exact question]

**Response:**

**Process Overview** (2-3 sentences):
Provide high-level summary of the overall process before diving into specifics.

Example: "Our patch management process identifies, assesses, tests, and deploys security patches across our infrastructure using a risk-based prioritization approach. Critical vulnerabilities follow an expedited process while standard patches deploy during planned maintenance windows. The process is governed by our Patch Management Procedure [version] and overseen by the Change Advisory Board."

**Detailed Responses to Each Sub-Question:**

**(1) [First sub-question repeated]**
[3-4 sentence response addressing specifically what was asked]
- Describe HOW you do this
- Reference WHAT tools/processes you use  
- Mention WHO is responsible
- Note WHEN this happens (frequency/triggers)

Evidence: [Specific artifacts that demonstrate this] - [Location/Reference]

**(2) [Second sub-question repeated]**
[Response addressing this specific point]

Evidence: [Relevant artifacts]

*[Continue for each sub-question]*

**Governance and Oversight:**
[1-2 sentences about management review, exceptions, continuous improvement]

Example: "The [ROLE/COMMITTEE] reviews patch management metrics [FREQUENCY], including mean time to patch, exception handling, and coverage rates. Exceptions to standard timelines require [APPROVAL_AUTHORITY] approval and are tracked in [SYSTEM]."

**Reference Documentation:**
- [Procedure name]: [Location/Version]
- [Policy name]: [Location/Version]
- [Other relevant documentation]

---

**RESPONSE QUALITY CHECKLIST** (use before finalizing):

**Completeness:**
- [ ] Every sub-question explicitly addressed
- [ ] No ambiguous or vague statements ("we generally..." "typically...")
- [ ] Specific tools, systems, or processes named (where appropriate)
- [ ] Roles and responsibilities clearly identified
- [ ] Timelines and frequencies specified

**Accuracy:**
- [ ] Every statement is factually true and can be verified
- [ ] Procedure references are correct (name, version, location)
- [ ] Evidence references are accurate and accessible
- [ ] No aspirational statements (what we plan to do vs. what we actually do)
- [ ] Consistent with procedure documentation

**Verifiability:**
- [ ] Evidence exists for each claim
- [ ] Evidence is accessible for auditor review
- [ ] References are specific enough for auditor to locate
- [ ] Metrics or examples provided where helpful

**Clarity:**
- [ ] Language appropriate for auditor (technical but audit-friendly)
- [ ] No unexplained acronyms or jargon
- [ ] Logical flow from overview to details
- [ ] Each paragraph addresses one concept

**Risk Management:**
- [ ] No unintended compliance commitments created
- [ ] Response aligns with what you can actually evidence
- [ ] Exceptions or limitations honestly noted
- [ ] No security vulnerabilities exposed in technical details

---

CRITICAL CONSTRAINTS:
- Use ONLY information you've provided about actual implementation
- Do NOT make up processes, tools, or evidence you don't have
- Do NOT assume implementation details not explicitly stated
- Do NOT include aspirational "we plan to" statements (auditor is evaluating current state)
- If implementation detail is missing, note: "[Requires input from [team] to confirm [specific detail]]"

TONE:
- Professional and confident (this is official audit record)
- Factual and specific (auditor needs to verify claims)
- Complete but concise (answer thoroughly without unnecessary detail)
- Helpful to auditor (make verification easy)

⚠️ ATTESTATION REMINDER:
This response becomes part of formal audit documentation. You are attesting to its accuracy. Every claim must be verifiable and true. When in doubt, verify with implementation team before submitting.
```

**🏢 Enterprise Tool Additions:**
- Name specific vendor tools and platforms
- Include specific version numbers where relevant
- Reference actual procedure documents by name and version
- Provide specific metric examples and timeframes
- Include actual committee or role names
- Reference specific file locations or systems

**🌐 Consumer Tool Restrictions:**
- Use tool categories not vendor names
- Omit version specifics unless publicly known
- Reference procedures generically
- Use metric types without specific numbers
- Use generic role titles
- Abstract file locations to general repository types

**Verification Checklist:**
- [ ] Every factual claim verified against actual implementation
- [ ] All procedure references are accurate (name, version, location)
- [ ] Evidence listed actually exists and is accessible
- [ ] Response consistent with documented procedures
- [ ] No claims made that cannot be supported with evidence
- [ ] Technical details reviewed by implementation team
- [ ] Appropriate stakeholders have reviewed and approved response

**Iteration Guidance:**
- If response seems incomplete: Identify which sub-questions weren't fully addressed
- If too technical: Add "Simplify for auditor with [background level]"
- If lacks specificity: Provide more implementation details (sanitized appropriately)
- If evidence weak: Note honestly: "Evidence for [aspect] is [limitation], we can provide [alternative]"

---
