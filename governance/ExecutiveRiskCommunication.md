## 5. Executive Risk Communication

**Task:** Translate technical security risk into executive decision-making document

**Advanced Techniques:** Audience-aware translation, decision framework presentation, scenario modeling

**Principles Applied:** Context (audience needs), Specificity (decision-focused), Structure (business impact framing)

```markdown
You are the CISO preparing a critical security risk communication for executive leadership. Your goal is to enable informed business decisions about risk treatment, not to create fear or dictate the decision.

TECHNICAL SECURITY SITUATION:
[Describe the technical security issue in detail]

Example: "Critical vulnerability ([CVE_NUMBER], CVSS [SCORE]) discovered in [SYSTEM/COMPONENT]. Exploit code is [publicly available/actively exploited/theoretical]. Patch available but requires [maintenance window/testing/system downtime]."

🏢 Enterprise: Be specific about your situation:
"CVE-2024-XXXXX (CVSS 9.8) in Apache Struts affects our customer portal application. Proof-of-concept exploit published [DATE]. Official patch available requiring 8-hour maintenance window for testing and deployment. Application processes [X transactions/day] generating [$Y revenue]."

🌐 Consumer: Keep details appropriately vague:
"Critical vulnerability in web application framework. Exploit code publicly available. Patch requires significant maintenance window. Application supports revenue-generating customer transactions."

BUSINESS CONTEXT:
- Timing: [Q4/Peak season/Critical business period/Normal operations]
- Business Impact of Downtime: [Revenue loss, customer impact, contract obligations]
  🏢 Enterprise: "Transaction processing: [X volume], [Y revenue/hour]. Major customer renewals in negotiation [specific accounts]. Planned downtime normally scheduled [Sunday 2-6am EST]."
  🌐 Consumer: "High transaction volume. Critical customer commitments in progress. Limited maintenance windows available."

- Recent Context: [Any relevant recent events]
  Example: "Unplanned outage [X weeks ago] frustrated customers and delayed [project/release]"

- Contractual Obligations: [SLAs, uptime commitments, customer notifications required]

EXECUTIVE DECISION-MAKERS:
Who needs to make this decision?
- CEO: [Focus] (e.g., customer/revenue/reputation impact)
- CFO: [Focus] (e.g., financial implications, cost-benefit)
- COO: [Focus] (e.g., operational continuity, resource allocation)
- [Other]: [Focus]

Decision Required: [What specific approval/decision are you seeking]
Example: "Approve emergency maintenance window [DATE/TIME] vs. delay until scheduled maintenance [DATE/TIME]"

---

COMMUNICATION TASK:

You will create TWO documents for different contexts:

## DOCUMENT 1: Executive Summary (1 page maximum)

This goes to the executive team for immediate decision-making.

**STRUCTURE REQUIRED:**

**1. SITUATION (2-3 sentences in business language)**
What happened? Why does it matter to the business?
- Avoid: "Critical CVE affecting Apache Struts framework"
- Use: "Our customer portal has a severe security vulnerability that attackers could exploit to [business impact in plain language]"

**2. BUSINESS RISK IF WE DON'T ACT (3-4 bullet points)**
What could happen if we delay until scheduled maintenance?
Think through:
- Likelihood: How probable is exploitation? (Consider: exploit availability, system exposure, attacker motivation)
- Business Impact: What's the worst-case scenario in business terms? (Revenue, customers, reputation, regulatory)
- Velocity: How quickly could this escalate from "vulnerability" to "actual breach"?

Frame in business language:
- ❌ "Potential for remote code execution and data exfiltration"
- ✅ "Attackers could access customer data, resulting in [specific business consequences]"

**3. OPTIONS ANALYSIS (Side-by-side comparison)**

Present 2-3 options with honest tradeoffs:

**Option A: Emergency Maintenance [Proposed Date/Time]**
- Security Benefit: [What this solves]
- Business Impact: [Revenue loss, customer inconvenience, resource cost]
- Tradeoff: [What we give up to gain security]

**Option B: Delayed Until Scheduled Maintenance [Date]**
- Security Risk: [Exposure window, probability of exploitation]
- Business Benefit: [Avoid disruption, maintain operations]
- Tradeoff: [What we risk to maintain operations]

**[Option C if applicable]**: [Alternative approach like compensating controls]

**4. RECOMMENDATION (2-3 sentences)**
What does the security team recommend and why?
- State your recommendation clearly
- Explain why based on risk/benefit tradeoff
- Acknowledge the business cost of your recommendation

Example: "We recommend Option A (emergency maintenance) because [risk assessment]. We recognize this impacts [business operations], but believe the risk of [X] outweighs the cost of [Y]. Similar vulnerabilities have been exploited within [timeframe] in our industry."

**5. IF YOU DECIDE DIFFERENTLY (1-2 sentences)**
What happens if executives choose a different option?
- No judgment, just facts
- Compensating controls we can implement
- Enhanced monitoring we'll provide
- Next decision point and timeline

**TONE FOR EXECUTIVE SUMMARY:**
- Clear and direct, no FUD (fear, uncertainty, doubt)
- Acknowledge business realities (revenue, customers, operations matter)
- Present as a business risk decision, not just a security issue
- Respect that executives weigh factors beyond security
- No technical jargon without explanation

---

## DOCUMENT 2: Board Risk Committee Slide (Single Slide)

This will be presented at the board's next risk committee meeting to provide governance oversight.

**SLIDE STRUCTURE (Use visual-friendly format):**

**Title**: [Clear risk description in business language]

**Left Column: Risk Scenario**
- What: [Vulnerability description in 1 sentence]
- Business Impact: [What could happen to the company]
- Likelihood: [Based on industry context and exploit availability]

**Middle Column: Options Considered**
| | Emergency Patch | Delayed Patch | [Other Option] |
|-----|-----|-----|-----|
| Security Risk | [Risk level] | [Risk level] | [Risk level] |
| Business Impact | [Impact description] | [Impact description] | [Impact description] |
| Cost | [Resources/downtime] | [Exposure window] | [Alternative cost] |

**Right Column: Management Decision & Rationale**
- Decision: [What executives decided]
- Rationale: [Why, in business risk terms]
- Current Status: [Implementation or monitoring status]
- Board Action Needed: [None/Awareness/Guidance on risk tolerance]

**Bottom: Industry Context**
"Similar vulnerabilities in [INDUSTRY] have been exploited within [TIMEFRAME]. [X%] of companies in our sector have experienced [CONSEQUENCE] from comparable risks. Our peer organizations are [action they're taking]."

**TONE FOR BOARD SLIDE:**
- Strategic/governance level, not tactical
- Frame in context of enterprise risk management
- Show management considered options carefully
- Demonstrate oversight is functioning
- Use visuals/tables, minimal text

---

CRITICAL CONSTRAINTS:
- Do NOT dictate the decision (you recommend, executives decide)
- Do NOT use fear-based language to manipulate decision-making
- Do NOT ignore business realities in favor of security perfection
- Do present honest tradeoffs with all options
- Do acknowledge when you're recommending something with business cost
- Do frame this as a business risk decision that requires business judgment

INFORMATION USE RESTRICTIONS:
- Use only information provided about the technical situation and business context
- If industry exploitation data isn't provided, note "[Requires current threat intelligence on exploitation rates]"
- If financial impact numbers aren't provided, note "[Requires business unit input on revenue/transaction impact]"
```

**🏢 Enterprise Tool Additions:**
- Include specific CVE numbers and CVSS scores
- Reference actual system names and business processes
- Provide real financial impact numbers (revenue/hour, transaction volumes)
- Name specific customer accounts or contracts at risk
- Include actual maintenance windows and schedules
- Reference specific past incidents by date

**🌐 Consumer Tool Restrictions:**
- Use generic vulnerability descriptions ("critical web application vulnerability")
- Abstract system names ("customer-facing application")
- Use relative financial impact ("significant revenue impact")
- Refer to generic customer categories
- Use timeframes without specific dates
- Reference generic industry incidents

**Verification Checklist:**
- [ ] Technical facts are accurate (CVE, CVSS, exploit status verified)
- [ ] Business impact numbers are confirmed with relevant business units
- [ ] Options presented are actually feasible with available resources
- [ ] Recommendation doesn't overstate or understate risk
- [ ] Language is appropriate for executive decision-making
- [ ] No fear-mongering or security pressure tactics used
- [ ] Business tradeoffs are honestly acknowledged

**Iteration Guidance:**
- If too technical: Add "Translate all technical terms for executives with no security background"
- If reads like pressure tactic: Add "Present neutrally - executives must weigh all business factors"
- If options seem incomplete: Provide more context about alternatives or constraints
- If business impact unclear: Specify "Focus on [revenue/customer/regulatory/reputation] impact specifically"

---
