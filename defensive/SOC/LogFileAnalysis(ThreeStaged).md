# Log Analysis Starter Prompts

A three-stage framework for analyzing security logs using AI tools, aligned with the four principles of effective AI prompting: Context, Specificity, Structure, and Iteration.

## Overview

These starter prompts guide you through comprehensive log analysis in three distinct stages:
1. **Stage 1: Analysis** - Deep examination of log patterns and anomalies
2. **Stage 2: Synthesis** - Risk assessment and correlation of findings
3. **Stage 3: Presentation** - Stakeholder-appropriate communication

Each stage builds on the previous one, allowing verification checkpoints and refinement between stages.

---

## How to Use These Prompts

1. **Customize the commented sections** (marked with `[MODIFY:]`) based on your specific needs
2. **Execute Stage 1** with your log data
3. **Review the analysis** output for accuracy and completeness
4. **Copy Stage 1 output** and use it as input for Stage 2
5. **Review the synthesis** for appropriate risk assessment
6. **Use Stage 2 output** as input for Stage 3
7. **Adjust the presentation** parameters based on your audience

**Important**: Each stage produces output that feeds the next stage. Do NOT skip stages or combine them into a single prompt.

---

## Stage 1: Log Analysis

### Purpose
Perform detailed pattern recognition and anomaly detection on log data without making risk judgments or recommendations. This stage focuses purely on what the logs show.

### The Prompt

```
You are a cybersecurity log analyst with expertise in pattern recognition and anomaly detection.

# ROLE CONTEXT [MODIFY: Adjust based on your actual role and responsibilities]
- I am a SOC analyst responsible for threat detection in a [MODIFY: your industry - e.g., "financial services", "healthcare", "technology"] environment
- My team has [MODIFY: "limited automation", "mature SIEM deployment", "manual log review processes"]
- I work in a [MODIFY: "24/7 SOC", "business hours security team", "hybrid operations model"]

# ENVIRONMENT CONTEXT [MODIFY: Describe your technical environment without exposing sensitive details]
- Infrastructure: [MODIFY: "cloud-native", "hybrid on-premises/cloud", "primarily on-premises", "multi-cloud"]
- Technology maturity: [MODIFY: "legacy systems", "modern infrastructure", "mixed environment with modernization roadmap"]
- Log aggregation: [MODIFY: "centralized SIEM", "distributed logging", "minimal log collection", "cloud-native logging"]

# CONSTRAINT CONTEXT [MODIFY: Specify your operational limitations]
- Time sensitivity: [MODIFY: "active incident investigation", "routine analysis", "historical review"]
- Data handling: [MODIFY: "sanitized logs only", "production data with approval", "test environment data"]
- Analysis scope: [MODIFY: "last 24 hours", "specific time window", "full dataset provided"]

# LOG TYPE & ANALYSIS OBJECTIVE [MODIFY: Critical - specify exactly what you're analyzing]
Log Type: [MODIFY: "authentication logs", "network traffic logs", "application logs", "firewall logs", "endpoint security logs", "cloud audit logs", etc.]

Analysis Objective: [MODIFY: Choose one or specify custom
- "Identify potential security incidents or anomalies"
- "Detect unauthorized access attempts"
- "Identify data exfiltration patterns"
- "Find indicators of lateral movement"
- "Detect configuration changes"
- "Identify compliance violations"
- Custom: "________________________________"]

# BASELINE INFORMATION [MODIFY: Optional but recommended - helps AI distinguish normal from abnormal]
Normal behavior in this environment includes:
- [MODIFY: "High volume of authentication during business hours (8 AM - 6 PM EST)"]
- [MODIFY: "Automated processes run at midnight and 3 AM daily"]
- [MODIFY: "Remote access from specific geographic regions (North America, Europe)"]
- [MODIFY: Add any other normal patterns specific to your environment]

Known false positive patterns to consider:
- [MODIFY: "Automated scanners from security tools generate expected alerts"]
- [MODIFY: "Legacy application generates authentication errors during normal operation"]
- [MODIFY: List any known sources of false positives]

# ANALYSIS INSTRUCTIONS

Analyze the provided log data with the following structure:

## 1. INITIAL ASSESSMENT
- Log source and type identification
- Time range covered
- Volume and completeness assessment
- Data quality observations

## 2. PATTERN IDENTIFICATION
Identify and document patterns observed in the logs:
- Temporal patterns (time-based trends, periodic activities)
- Source patterns (systems, users, geographic locations)
- Behavioral patterns (sequences of events, correlated activities)
- Volume patterns (spikes, dips, sustained levels)

## 3. ANOMALY DETECTION
Identify deviations from expected behavior:
- Unusual source/destination combinations
- Off-hours activities (if not expected)
- Unexpected authentication patterns
- Configuration changes
- Error patterns
- Failed operations
- Geographic anomalies

## 4. TECHNICAL DETAILS EXTRACTION
For each significant finding, document:
- Timestamp(s)
- Source identifier (IP, username, system - sanitized if needed)
- Event type/action
- Result/status
- Relevant fields from log entries
- Frequency of occurrence

## 5. CORRELATION OBSERVATIONS
Note relationships between events:
- Sequential events that may be related
- Concurrent activities across different sources
- Patterns that span multiple log entries
- Event chains that tell a story

# OUTPUT FORMAT [MODIFY: Adjust detail level based on your needs]
Detail Level: [MODIFY: "high detail for investigation", "moderate detail for review", "summary level for overview"]

Organize your analysis using this structure:
1. Executive Summary (3-5 sentences)
2. Detailed Findings (organized by pattern type)
3. Technical Evidence (specific log entries supporting findings)
4. Correlation Matrix (relationships between findings)
5. Questions Requiring Clarification (ambiguities or gaps)

# CRITICAL INSTRUCTIONS
- DO NOT assess risk levels or severity (this happens in Stage 2)
- DO NOT make recommendations (this happens in Stage 2)
- DO NOT assume malicious intent - report observations objectively
- DO identify patterns that deviate from baseline
- DO note confidence levels for findings (high/medium/low confidence based on log evidence)
- DO preserve technical accuracy over readability
- DO flag when log data is incomplete or ambiguous

---

[PASTE LOG DATA BELOW THIS LINE OR ATTACH TO PROMPT]

```

---

## Stage 2: Risk Synthesis & Correlation

### Purpose
Transform the analytical findings from Stage 1 into risk-assessed insights and actionable intelligence. This stage adds context about threats, correlates findings, and evaluates business impact.

### The Prompt

```
You are a cybersecurity threat analyst specializing in risk assessment and security correlation.

# ROLE CONTEXT [MODIFY: Adjust based on your actual role]
- I am a [MODIFY: "security analyst", "threat hunter", "incident responder", "security engineer"]
- My responsibility is [MODIFY: "threat detection and response", "security monitoring", "vulnerability management"]
- I report to [MODIFY: "security operations manager", "CISO", "IT director"]

# ORGANIZATIONAL CONTEXT [MODIFY: Critical for appropriate risk assessment]
Risk Tolerance: [MODIFY: "low - heavily regulated industry", "moderate - balanced approach", "high - fast-moving startup"]

Business Impact Considerations:
- [MODIFY: "Patient safety is paramount (healthcare)"]
- [MODIFY: "Financial data protection is critical (financial services)"]
- [MODIFY: "Service availability drives business (SaaS)"]
- [MODIFY: "Intellectual property protection is essential (technology)"]

Compliance Requirements:
- [MODIFY: "HIPAA", "PCI-DSS", "SOC 2", "GDPR", "None specific", "Multiple frameworks"]

# THREAT CONTEXT [MODIFY: Specify your threat landscape]
Known Threat Actors Targeting Our Sector:
- [MODIFY: List any known threat actors or campaigns relevant to your industry, or state "General threat landscape"]

Recent Threat Intelligence:
- [MODIFY: "Increase in ransomware targeting our sector"]
- [MODIFY: "Active credential stuffing campaigns"]
- [MODIFY: "No specific current threats identified"]

Our Historical Incidents:
- [MODIFY: "Previous phishing compromise in Q2"]
- [MODIFY: "Attempted ransomware deployment last year"]
- [MODIFY: "No significant incidents"]
- [MODIFY: "Cannot disclose - assess based on general threat landscape"]

# SYNTHESIS INSTRUCTIONS

Using the analysis from Stage 1 (provided below), perform the following synthesis:

## 1. RISK ASSESSMENT
For each significant finding from Stage 1:
- Assign risk level: [MODIFY: Choose your scale - "Critical/High/Medium/Low", "1-5 scale", "Red/Yellow/Green"]
- Justify the risk level based on:
  * Likelihood of malicious intent
  * Potential business impact
  * Deviation from baseline
  * Correlation with known attack patterns
  * Environmental context

## 2. THREAT CORRELATION
Evaluate findings against known attack patterns:
- Does this match known Tactics, Techniques, and Procedures (TTPs)?
- Could this be part of a multi-stage attack?
- Are there indicators suggesting reconnaissance, lateral movement, or exfiltration?
- What is the confidence level for each correlation?

## 3. FALSE POSITIVE ASSESSMENT
For each finding, evaluate the likelihood this is benign:
- Could this be legitimate business activity?
- Does this match known false positive patterns?
- What additional evidence would confirm or refute malicious intent?

## 4. IMPACT ANALYSIS
Assess potential impact if findings represent actual threats:
- Systems or data potentially affected
- Business processes that could be disrupted
- Compliance implications
- Stakeholder impact

## 5. TEMPORAL ANALYSIS
Evaluate the timeline:
- Is this an ongoing issue or historical?
- What is the urgency level?
- Are there signs of progression or escalation?

## 6. RECOMMENDATIONS
Generate prioritized recommendations:
- Immediate actions (if any)
- Short-term investigation steps
- Long-term improvements
- Additional data needed for conclusive assessment

# OUTPUT FORMAT [MODIFY: Adjust based on your workflow]
Organize your synthesis using this structure:
1. Executive Summary (risk level, key findings, urgency)
2. Prioritized Findings (ordered by risk level)
3. Threat Intelligence Correlation
4. Impact Assessment
5. Recommended Actions (categorized by timeframe)
6. Investigation Gaps (what additional information is needed)

Priority Order: [MODIFY: "Risk-based", "Chronological", "Business impact-based"]

# CRITICAL INSTRUCTIONS
- Risk assessments must consider both likelihood AND impact
- Distinguish between confirmed threats and potential threats
- Provide confidence levels for all assessments
- Consider the operational context from Stage 1
- Recommendations must be actionable and specific
- Flag uncertainties explicitly - don't guess

---

[PASTE THE COMPLETE OUTPUT FROM STAGE 1 BELOW THIS LINE]

```

---

## Stage 3: Stakeholder Presentation

### Purpose
Transform the technical analysis and risk synthesis into clear, actionable communication appropriate for your specific audience. This stage focuses on clarity, appropriate detail level, and decision support.

### The Prompt

```
You are a cybersecurity communications specialist skilled at translating technical security findings into stakeholder-appropriate formats.

# AUDIENCE CONTEXT [MODIFY: Critical - this determines tone, detail, and focus]
Primary Audience: [MODIFY: Choose one
- "Executive leadership (CEO, CFO, Board)" 
- "CISO / Security leadership"
- "Security operations team"
- "IT operations team"
- "Legal / Compliance team"
- "Business unit leaders"
- "Technical engineers / developers"
- Mixed audience: "________________________"]

Audience Technical Level: [MODIFY: "Non-technical business focus", "Mixed technical literacy", "Highly technical"]

Audience Primary Concern: [MODIFY:
- "Business risk and impact"
- "Compliance and regulatory"
- "Operational continuity"
- "Technical remediation"
- "Budget and resources"
- "Timeline and urgency"]

# PRESENTATION CONTEXT [MODIFY: Shapes format and emphasis]
Communication Purpose: [MODIFY:
- "Inform of incident or anomaly"
- "Request decision or approval"
- "Provide status update"
- "Document for compliance"
- "Share threat intelligence"
- "Request resources or budget"]

Time Pressure: [MODIFY: "Active incident - urgent", "Elevated concern", "Routine reporting", "Historical documentation"]

Organizational Culture: [MODIFY: "Prefers detailed documentation", "Values brevity and action items", "Data-driven decision making", "Risk-averse", "Balanced approach"]

# PRESENTATION INSTRUCTIONS

Transform the synthesis from Stage 2 (provided below) into a clear, actionable presentation:

## 1. EXECUTIVE SUMMARY [MODIFY: Length based on audience]
Create a [MODIFY: "2-3 sentence", "single paragraph", "bullet point"] summary that includes:
- What was found (at appropriate detail level)
- Why it matters (business impact)
- What happens next (clear next steps)
- When action is needed (timeline/urgency)

## 2. KEY FINDINGS
Present findings at the appropriate detail level:

For Executive Audiences:
- Focus on business impact, not technical details
- Use risk language ("this could lead to...", "potential for...")
- Quantify impact where possible
- Avoid jargon and acronyms

For Technical Audiences:
- Include specific technical details
- Reference frameworks and standards
- Provide implementation specifics
- Use appropriate technical terminology

For Mixed Audiences:
- Use a layered approach (summary + technical appendix)
- Define technical terms when first used
- Balance business context with technical accuracy

## 3. IMPACT ASSESSMENT [MODIFY: Emphasis based on audience]
Present impact in terms your audience cares about:
- [MODIFY: Financial impact estimates? Yes/No]
- [MODIFY: Regulatory/compliance implications? Yes/No]
- [MODIFY: Reputational risk? Yes/No]
- [MODIFY: Operational disruption? Yes/No]
- [MODIFY: Customer impact? Yes/No]

## 4. RECOMMENDED ACTIONS
Format recommendations appropriately:

Decision Required: [MODIFY: Yes/No - if yes, be explicit about what decision is needed]

Action Items Format: [MODIFY:
- "Prioritized list with owners and timelines"
- "Categorized by timeframe (Immediate/Short-term/Long-term)"
- "Grouped by responsible team"
- "Risk-based priority order"]

Resource Requirements: [MODIFY: "Include budget/resource needs", "Focus on internal resources", "No resource discussion needed"]

## 5. SUPPORTING DETAILS [MODIFY: Level of detail]
Include: [MODIFY: Select what to include
- "Technical evidence in appendix"
- "Timeline of events"
- "Comparison to industry benchmarks"
- "Relevant compliance frameworks"
- "Cost-benefit analysis"
- "Risk matrix visualization"
- "Minimal supporting detail"]

# OUTPUT FORMAT [MODIFY: Choose format appropriate for your organization]
Format Style: [MODIFY:
- "Formal report with sections and subsections"
- "Executive brief (1-2 pages max)"
- "Bullet-point memo"
- "Email format"
- "Presentation slides structure"
- "Incident ticket format"
- "Compliance documentation format"]

Tone: [MODIFY: "Formal and precise", "Professional but conversational", "Technical and detailed", "Urgent and action-oriented"]

Length Target: [MODIFY: "1 page", "2-3 pages", "Comprehensive documentation", "As concise as possible"]

# FORMATTING PREFERENCES [MODIFY: Organizational standards]
- Use headers: [MODIFY: Yes/No]
- Use bullet points: [MODIFY: Yes/No - or "Only for action items"]
- Use bold for emphasis: [MODIFY: Yes/No - or "Sparingly"]
- Include visual elements: [MODIFY: "Yes, suggest charts/diagrams", "No, text only"]
- Include glossary: [MODIFY: Yes/No]

# CRITICAL INSTRUCTIONS
- Match detail level to audience technical literacy
- Lead with what matters most to this audience
- Be clear about what requires decision vs. information
- Distinguish facts from assessments
- Provide appropriate context without overwhelming
- Make action items specific and achievable
- Include confidence levels for uncertain findings
- Avoid fear-mongering while communicating real risks

---

[PASTE THE COMPLETE OUTPUT FROM STAGE 2 BELOW THIS LINE]

```

---

## Iteration Guidance

### When to Iterate

After each stage, assess whether the output meets your needs:

**Stage 1 Iteration Triggers:**
- Analysis is too generic or high-level
- Missing specific pattern types relevant to your environment
- Insufficient technical detail for verification
- False negatives (missed something you see in the logs)
- False positives (flagged known-good activity)

**Stage 2 Iteration Triggers:**
- Risk levels don't align with your threat model
- Missing correlation with recent threat intelligence
- Recommendations aren't actionable in your environment
- Impact assessment doesn't reflect business priorities
- Confidence levels unclear or unjustified

**Stage 3 Iteration Triggers:**
- Wrong tone or detail level for audience
- Key concerns not addressed
- Action items unclear or unassigned
- Format doesn't match organizational standards
- Missing elements required for decision-making

### How to Refine

**For more specificity:**
"In your analysis of [specific finding], provide more detail about [specific aspect]. Include [specific data points or patterns]."

**For different perspective:**
"Re-evaluate [specific finding] considering [additional context you provide]. How does this change your assessment?"

**For focus adjustment:**
"Your analysis covers [broad area]. Narrow focus to [specific subset] and provide deeper analysis there."

**For context correction:**
"You interpreted [pattern] as [their interpretation]. In our environment, [provide correcting context]. Re-assess this finding."

---

## Examples & Best Practices

### Good Context Examples

✅ **Good**: "I'm a SOC analyst in a healthcare environment subject to HIPAA. We have limited automation and a small security team supporting 24/7 operations."

❌ **Too Vague**: "I work in security."

✅ **Good**: "Our environment uses hybrid infrastructure with cloud-native applications and legacy on-premises systems undergoing modernization."

❌ **Too Specific**: "We run AWS with EC2 instances at 10.50.0.0/16 and use Cisco ASA firewalls version 9.14."

### Good Specificity Examples

✅ **Good**: "Analyze these authentication logs for failed login patterns indicating credential stuffing, focusing on the last 48 hours during business hours (8 AM - 6 PM EST)."

❌ **Too Vague**: "Look at these logs and tell me if anything is wrong."

✅ **Good**: "For each finding, document: timestamp, source IP, destination system, event type, frequency, and confidence level (high/medium/low)."

❌ **Too Vague**: "Document what you find."

### Good Structure Examples

✅ **Good**: Using the three-stage approach with verification between stages

❌ **Poor**: Combining all three stages into one massive prompt

✅ **Good**: Separating analysis (Stage 1) from risk assessment (Stage 2)

❌ **Poor**: Asking for analysis with risk levels mixed together

---

## Troubleshooting

### Common Issues

**Issue**: AI is hallucinating log entries or patterns not in your data
**Solution**: Add to Stage 1: "Base your analysis ONLY on the log entries provided. Do not infer or generate log entries. If you reference a pattern, cite specific line numbers or timestamps from the provided logs."

**Issue**: Risk assessments too conservative or too aggressive
**Solution**: Refine Stage 2 risk tolerance context. Add examples: "In our environment, [specific scenario] would be considered [risk level] because [reasoning]."

**Issue**: Output uses wrong terminology for your organization
**Solution**: Add terminology guidance: "Use our organization's terminology: we call [their term] '[your term]'. We classify risks as [your classification system]."

**Issue**: Analysis misses context about your normal operations
**Solution**: Expand baseline information in Stage 1. Be more specific about what's normal: "Every day at 2 AM, automated backup processes generate [specific log patterns]. This is expected and should not be flagged."

**Issue**: Recommendations aren't actionable in your environment
**Solution**: Add constraints to Stage 2: "We cannot [specific limitation]. Recommendations must work within constraints of [your specific constraints]."

---

## Version Control & Customization

### Saving Your Customized Prompts

1. **Copy this template** to your own document
2. **Make your modifications** in the [MODIFY:] sections
3. **Test with sample log data** (use sanitized/test data first)
4. **Refine based on results**
5. **Save your customized version** with your organization's specific context
6. **Version your templates** as you improve them
7. **Share with your team** to ensure consistency

### Template Versioning Example

```
# Log Analysis Template v1.2
# Last Updated: 2024-11-15
# Changes: Added baseline for automated backups, refined risk tolerance context
# Tested on: Authentication logs, firewall logs
# Team: SOC Alpha
```

---

## Security & Privacy Considerations

### Before Using These Prompts

**✅ DO:**
- Sanitize logs before submitting to AI tools (remove sensitive IPs, usernames, system names)
- Use enterprise AI instances with data processing agreements
- Review your organization's AI usage policy
- Document your verification steps
- Treat AI output as a draft requiring validation

**❌ DON'T:**
- Submit unredacted production logs to consumer AI tools
- Include actual credentials, API keys, or secrets
- Trust AI output without verification
- Skip verification because the output "looks good"
- Use AI for decisions requiring legal accountability

### Data Sanitization Quick Guide

**Before submitting logs, sanitize:**
- Replace real IP addresses with placeholders (e.g., USER_IP_1, INTERNAL_SYSTEM_A)
- Replace usernames with generic identifiers (e.g., USER_001, ADMIN_USER_B)
- Replace domain names with placeholders (e.g., COMPANY_DOMAIN, EXTERNAL_DOMAIN_1)
- Remove any PII, credentials, or sensitive configuration details
- Preserve the pattern and structure of the data

**Example:**
```
# Original
2024-11-06 10:23:15 192.168.50.100 john.smith@company.com LOGIN_FAILED from 203.0.113.42

# Sanitized
2024-11-06 10:23:15 INTERNAL_IP_1 USER_001@COMPANY_DOMAIN LOGIN_FAILED from EXTERNAL_IP_1
```

---

## Integration with Your Workflow

### Recommended Workflow

1. **Log Collection**: Gather relevant logs for the time period and scope
2. **Sanitization**: Remove sensitive information while preserving patterns
3. **Stage 1 Execution**: Run analytical prompt, review output
4. **Verification Checkpoint**: Validate Stage 1 findings against raw logs
5. **Stage 2 Execution**: Run synthesis prompt with Stage 1 output
6. **Verification Checkpoint**: Validate risk assessments and recommendations
7. **Stage 3 Execution**: Run presentation prompt with Stage 2 output
8. **Final Review**: Ensure output meets audience needs and organizational standards
9. **Human Validation**: Have appropriate stakeholder review before distribution
10. **Documentation**: Save your prompts, outputs, and verification notes

### Quality Checkpoints

After Stage 1:
- [ ] All significant patterns identified?
- [ ] Technical details accurate?
- [ ] False positives noted?
- [ ] Baseline deviations clear?

After Stage 2:
- [ ] Risk levels appropriate for your context?
- [ ] Threat correlations accurate?
- [ ] Recommendations actionable?
- [ ] Impact assessment aligned with business priorities?

After Stage 3:
- [ ] Appropriate for audience?
- [ ] Clear action items?
- [ ] Correct tone and format?
- [ ] Decision points explicit?

---

## Contributing

If you develop improvements to these prompts:
1. Document what you changed and why
2. Note which types of logs/scenarios it works well for
3. Share back to help others
4. Include your testing methodology

---

## License & Attribution

[Add your license information]

Based on the four principles framework from "Prompt Thinking for Security Professionals" - Context, Specificity, Structure, and Iteration.

---

## Support & Questions

[Add your contact/support information]

**Remember**: These are starter templates. Your specific environment, threat model, and organizational needs will require customization. The [MODIFY:] sections are guidance, not rules. Adapt these prompts to serve your actual security work.
