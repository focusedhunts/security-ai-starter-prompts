## 4. Risk Register Entry with Impact Analysis

**Task:** Document risk scenario with structured impact analysis and treatment recommendations

**Advanced Techniques:** Impact scenario modeling, decision framework application, chain-of-thought reasoning

**Principles Applied:** Context (risk methodology), Structure (consistent entry format), Specificity (rating criteria)

```markdown
You are a risk analyst documenting a newly identified security risk using our enterprise risk management framework. Your analysis will inform executive decision-making about risk treatment.

RISK SCENARIO TO DOCUMENT:
[Describe the risk situation in 2-3 sentences]

Example: "Third-party vendor providing [SERVICE_TYPE] experienced a data breach. Vendor has access to [DATA_TYPES]. Vendor's security practices appear weaker than our requirements based on [recent assessment/security questionnaire/incident notification]."

🏢 Enterprise: Be specific about the scenario:
"Acme Corp, our customer support ticketing vendor, notified us of a breach exposing [specific data types]. They have API access to our customer database (read-only). Their last security assessment was 18 months ago and showed [specific concerns]."

🌐 Consumer: Keep scenario generic:
"Third-party service provider experienced a security incident. They process [general data category]. Security assessment conducted [timeframe] identified potential concerns."

ORGANIZATIONAL RISK CONTEXT:
- Industry: [SECTOR] with [REGULATORY_ENVIRONMENT]
- Risk Culture: [RISK_AVERSE / MODERATE / RISK_TOLERANT]
- Risk Methodology: [QUALITATIVE / QUANTITATIVE / HYBRID]
  Use: [LOW/MEDIUM/HIGH/CRITICAL] or [1-5 scale] or [$ impact ranges]

RISK RATING METHODOLOGY:
Define your organization's criteria clearly so AI can apply them consistently:

**LIKELIHOOD ASSESSMENT CRITERIA:**
- CRITICAL/5: Near certain to occur ([>X%] annual probability or [specific indicators])
- HIGH/4: Likely to occur ([X-Y%] probability or [specific indicators])
- MEDIUM/3: Possible to occur ([X-Y%] probability or [specific indicators])
- LOW/2: Unlikely to occur ([X-Y%] probability or [specific indicators])
- MINIMAL/1: Rare occurrence ([<X%] probability or [specific indicators])

**IMPACT ASSESSMENT CRITERIA:**
Define impact across dimensions that matter to your organization:
- Financial: [$ ranges for each severity level]
- Operational: [Description of disruption for each level]
- Reputational: [Description of brand/trust impact]
- Regulatory: [Description of compliance consequences]
- [Other dimensions relevant to your industry]

Example Impact Levels:
- CRITICAL: [>$5M] financial loss OR [major regulatory penalty] OR [significant operational disruption >X days]
- HIGH: [$1M-$5M] loss OR [regulatory investigation] OR [moderate disruption X-Y days]
- MEDIUM: [$250K-$1M] loss OR [regulatory inquiry] OR [minor disruption <X days]
- LOW: [<$250K] loss OR [minimal regulatory attention] OR [negligible disruption]

EXISTING CONTROLS (if any):
List controls currently in place that reduce this risk:
- [Control 1 description]
- [Control 2 description]
- [Control 3 description]

🏢 Enterprise: Be specific:
"Annual vendor security assessments conducted. Contract includes security requirements and right-to-audit clause. Vendor data access is read-only via API with rate limiting. Data encrypted in transit (TLS 1.3) and at rest (AES-256)."

🌐 Consumer: Keep generic:
"Periodic vendor assessments performed. Contractual security requirements in place. Technical access controls implemented. Encryption standards enforced."

---

RISK ANALYSIS TASK:

Think through this risk systematically using our methodology:

**STEP 1: THREAT AND VULNERABILITY ANALYSIS**
Based on the scenario:
- Threat Source: What could cause this risk to materialize? (threat actor, system failure, human error, external event)
- Vulnerable Asset: What specific asset/system/process is at risk?
- Attack Vector / Failure Mode: How would this risk materialize?

**STEP 2: INHERENT RISK RATING (before existing controls)**
If we had NO controls in place:
- Likelihood Rating: [RATING] - Justify based on our likelihood criteria
- Impact Rating: [RATING across each dimension] - Justify based on our impact criteria
- Inherent Risk Score: [LIKELIHOOD × HIGHEST_IMPACT]

Think through: "Without any controls, how likely and how severe would this be?"

**STEP 3: CONTROL EFFECTIVENESS ASSESSMENT**
For each existing control listed:
- How effective is it? (Highly Effective / Moderately Effective / Limited Effectiveness / Ineffective)
- Why? (What does it prevent? What doesn't it prevent?)

**STEP 4: RESIDUAL RISK RATING (with existing controls)**
Given our current controls:
- Residual Likelihood: [RATING] - How have controls reduced probability?
- Residual Impact: [RATING] - How have controls reduced consequences?
- Residual Risk Score: [RESIDUAL_LIKELIHOOD × RESIDUAL_IMPACT]

**STEP 5: RISK TREATMENT RECOMMENDATION**
Based on residual risk level, recommend one treatment approach:

- **ACCEPT**: Residual risk is within tolerance, no further action needed
  - Justification: [Why this level is acceptable]
  - Monitoring: [How we'll track this risk]

- **MITIGATE**: Implement additional controls to reduce risk
  - Proposed Controls: [Specific additional controls to implement]
  - Expected Risk Reduction: [New likelihood/impact after mitigation]
  - Implementation Cost/Effort: [Resources required]
  - Target Completion: [Timeline]

- **TRANSFER**: Share/transfer risk to third party (insurance, outsourcing)
  - Transfer Mechanism: [Insurance policy, contractual liability shift, etc.]
  - Cost of Transfer: [Premium, contract terms]
  - Residual Risk After Transfer: [What remains our responsibility]

- **AVOID**: Eliminate the risk by discontinuing activity
  - Avoidance Action: [Stop using vendor, shut down system, etc.]
  - Business Impact of Avoidance: [What capability do we lose]
  - Alternative Solutions: [How to achieve business objective differently]

---

OUTPUT FORMAT (Risk Register Entry):

**RISK ID**: [Auto-generated or use your numbering scheme]
**Risk Title**: [Concise, clear title in business language]
**Date Identified**: [DATE]

**Risk Description** (2-3 sentences in business language):
[What is the risk? What could happen? Who/what is affected?]

**Threat Source**: [What causes this risk]
**Vulnerable Asset**: [What's at risk]
**Attack Vector / Failure Mode**: [How risk materializes]

**Inherent Risk Assessment** (before controls):
- Likelihood: [RATING] - [Justification]
- Impact: [RATING] - [Justification across dimensions]
- Inherent Risk Score: [SCORE]

**Existing Controls**:
- [Control 1 with effectiveness assessment]
- [Control 2 with effectiveness assessment]
- [Control 3 with effectiveness assessment]

**Residual Risk Assessment** (with current controls):
- Likelihood: [RATING] - [Justification]
- Impact: [RATING] - [Justification]
- Residual Risk Score: [SCORE]

**Risk Treatment Recommendation**: [ACCEPT/MITIGATE/TRANSFER/AVOID]
[Detailed justification and action plan based on your Step 5 analysis]

**Risk Owner**: [ROLE_TITLE] (person with authority to accept or treat this risk)
**Target Risk Level**: [After treatment, where do we want this risk to be]
**Review Frequency**: [How often should this risk be reassessed]
**Next Review Date**: [DATE]

CRITICAL CONSTRAINTS:
- Provide business-appropriate language (executives make risk decisions, not just security team)
- Base recommendations only on information provided (don't assume organizational risk tolerance)
- If recommending ACCEPT, clearly state why residual risk is tolerable
- If recommending MITIGATE, proposed controls must be specific and implementable
- Risk owner must be role with actual authority to accept/treat risk (CISO, Business Unit Owner, etc.)
```

**🏢 Enterprise Tool Additions:**
- Name specific vendors, systems, and data types involved
- Reference your actual risk rating scale and thresholds
- Include specific $ amounts for financial impact
- Reference actual controls and their implementation details
- Name the actual risk owner role

**🌐 Consumer Tool Restrictions:**
- Use generic vendor/system/data categories
- Use relative impact scales (High/Medium/Low) without $ specifics
- Describe controls generically without implementation details
- Use generic role titles for risk ownership

**Verification Checklist:**
- [ ] Risk ratings applied consistently per defined methodology
- [ ] Existing controls listed actually exist and are documented
- [ ] Impact assessment realistic across all relevant dimensions
- [ ] Treatment recommendation aligned with organizational risk tolerance
- [ ] Risk owner has actual authority to make treatment decisions
- [ ] Supporting evidence available for all factual claims

**Iteration Guidance:**
- If risk ratings seem off: Clarify your likelihood/impact criteria more explicitly
- If treatment recommendation doesn't fit: Provide more context about organizational priorities
- If too technical: Add "Explain for executives who need to make business risk decisions"
- If control effectiveness unclear: Provide more details about what controls actually prevent

---
