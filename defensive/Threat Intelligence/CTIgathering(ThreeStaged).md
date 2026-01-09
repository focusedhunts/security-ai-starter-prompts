# Threat Intelligence Research Starter Prompts

A three-stage framework for conducting threat intelligence research using AI tools, aligned with the four principles of effective AI prompting: Context, Specificity, Structure, and Iteration.

## Overview

These starter prompts guide you through comprehensive threat intelligence research in three distinct stages:
1. **Stage 1: Intelligence Gathering** - Collect and organize threat data from multiple perspectives
2. **Stage 2: Analysis & Correlation** - Synthesize findings, map TTPs, and assess relevance
3. **Stage 3: Actionable Intelligence** - Transform analysis into defensive recommendations

Each stage builds on the previous one, allowing verification checkpoints and refinement between stages. This approach leverages AI's pattern recognition and synthesis capabilities while maintaining human judgment for risk assessment and strategic decisions.

---

## How to Use These Prompts

1. **Customize the commented sections** (marked with `[MODIFY:]`) based on your intelligence requirements
2. **Execute Stage 1** with your research objective
3. **Review the gathered intelligence** for accuracy and relevance
4. **Copy Stage 1 output** and use it as input for Stage 2
5. **Verify the analysis** against authoritative sources (MITRE ATT&CK, vendor reports)
6. **Use Stage 2 output** as input for Stage 3
7. **Validate recommendations** against your defensive capabilities before implementation

**Important**: Threat intelligence from AI requires verification. Always cross-reference findings with authoritative sources. AI excels at synthesis but can hallucinate threat actors, TTPs, or IOCs that don't exist.

---

## Stage 1: Intelligence Gathering

### Purpose
Collect comprehensive threat intelligence from multiple angles without making judgments about relevance or priority. This stage focuses on gathering information about threat actors, campaigns, TTPs, and targeting patterns.

### The Prompt

```
You are a threat intelligence researcher specializing in gathering and organizing information about cybersecurity threats, threat actors, and attack campaigns.

# ROLE CONTEXT [MODIFY: Adjust based on your actual role and responsibilities]
- I am a [MODIFY: "threat intelligence analyst", "security researcher", "SOC analyst", "threat hunter"]
- My primary responsibility is [MODIFY: "proactive threat research", "incident response support", "defensive strategy", "threat hunting"]
- I support [MODIFY: "a SOC team", "security operations", "executive decision-making", "defensive security controls"]

# ORGANIZATIONAL CONTEXT [MODIFY: Critical for filtering relevant intelligence]
Industry/Sector: [MODIFY: "Financial Services", "Healthcare", "Technology/SaaS", "Manufacturing", "Critical Infrastructure", "Government", "Retail", "Education"]

Organization Size: [MODIFY: "Small (<500 employees)", "Mid-size (500-5000)", "Large (5000+)", "Enterprise (50,000+)"]

Geographic Focus: [MODIFY: "North America", "Europe", "Asia-Pacific", "Global operations", "Specific region: _______"]

Technology Stack Characteristics: [MODIFY: "Cloud-native (AWS/Azure/GCP)", "Hybrid infrastructure", "Primarily on-premises", "Microsoft-centric", "Linux/open-source focused", "Multi-cloud"]

# THREAT CONTEXT [MODIFY: Helps focus research on relevant threats]
Our Threat Landscape:
- Known previous incidents: [MODIFY: "Ransomware attempt in past year", "Phishing campaigns", "Insider threat", "No significant incidents", "Cannot disclose"]
- Current security concerns: [MODIFY: "Supply chain risk", "Ransomware", "Nation-state threats", "Cybercrime", "Insider threats", "All threat types"]
- Specific vulnerabilities of concern: [MODIFY: "Legacy systems", "Remote workforce", "Cloud adoption", "OT/ICS systems", "Third-party integrations"]

# INTELLIGENCE REQUIREMENTS [MODIFY: Be specific about what you're researching]

Research Objective: [MODIFY: Choose one or specify custom
- "Profile a specific threat actor or group"
- "Research a threat campaign or operation"
- "Investigate threats targeting our industry"
- "Analyze a specific malware family or tool"
- "Understand emerging attack techniques"
- "Track a specific vulnerability being exploited"
- Custom: "________________________________"]

Specific Focus: [MODIFY: Be as specific as possible]
- Threat Actor/Group: [MODIFY: "APT29", "Scattered Spider", "LockBit", "Unknown actor - describe observed TTPs", "Industry-targeting actors generally"]
- Campaign Name: [MODIFY: Specific operation name if known, or "Recent campaigns targeting our sector"]
- Malware/Tool: [MODIFY: "Specific malware family", "Ransomware variants", "Living-off-the-land techniques", "Initial access methods"]
- Technique: [MODIFY: MITRE ATT&CK technique ID if known, or describe: "Credential theft via cloud services", "Supply chain compromise"]
- Timeframe: [MODIFY: "Last 30 days", "Last quarter", "Past year", "Historical analysis", "Ongoing campaign"]

# INTELLIGENCE COLLECTION SCOPE [MODIFY: Define boundaries]

Geographic Scope: [MODIFY: "Global intelligence", "Specific regions: _______", "Exclude regions: _______"]

Source Types to Consider: [MODIFY: Select relevant sources
- "Government/CISA advisories"
- "Vendor threat reports (CrowdStrike, Mandiant, etc.)"
- "MITRE ATT&CK framework"
- "Open-source intelligence (OSINT)"
- "Information sharing communities (ISACs)"
- "Academic research"
- "Dark web/underground forums" (describe with caution, no illegal access)
- All authoritative public sources]

Information Categories: [MODIFY: Select what's most relevant
- "Threat actor attribution and motivations"
- "Tactics, Techniques, and Procedures (TTPs)"
- "Indicators of Compromise (IOCs)"
- "Target selection criteria"
- "Attack lifecycle and kill chain"
- "Tools and infrastructure"
- "Victimology and impact"
- All categories]

# BASELINE KNOWLEDGE [MODIFY: Optional - helps AI build on what you know]
What we already know:
- [MODIFY: "We've observed reconnaissance activity from IP ranges associated with ________"]
- [MODIFY: "Our sector has been targeted by ________ in the past"]
- [MODIFY: "We know this threat actor typically uses ________ for initial access"]
- [MODIFY: "Starting research from scratch - no prior knowledge"]

What we need to learn:
- [MODIFY: "How does this threat actor move laterally?"]
- [MODIFY: "What are early warning indicators we should monitor?"]
- [MODIFY: "What defensive measures have been effective?"]
- [MODIFY: "How does this threat differ from similar threats?"]

# RESEARCH INSTRUCTIONS

Gather comprehensive threat intelligence using the following structure:

## 1. THREAT OVERVIEW
Provide a comprehensive overview including:
- Threat identification (names, aliases, tracking identifiers)
- First observed / discovery timeframe
- Evolution and timeline of significant activity
- Current activity status (active, dormant, evolved)
- Classification (APT, cybercrime, hacktivism, insider threat)

## 2. ATTRIBUTION & MOTIVATION
Document what is known about:
- Attribution (who - state-sponsored, criminal group, individual)
- Suspected nation-state or organizational affiliation (if applicable)
- Motivation (financial gain, espionage, disruption, ideology)
- Confidence level in attribution (high/medium/low - cite sources)
- Controversy or debate in attribution

## 3. TARGET PROFILE
Identify targeting patterns:
- Industries and sectors targeted
- Geographic targeting preferences
- Organization size/type preferences
- Specific technologies or systems targeted
- Target selection criteria or opportunistic approach
- Victimology patterns

## 4. TACTICS, TECHNIQUES, AND PROCEDURES (TTPs)

Map observed behaviors to MITRE ATT&CK framework where applicable:

### Initial Access
- Techniques used (phishing, exploits, stolen credentials, supply chain)
- Common lures or social engineering approaches
- Exploit preferences
- MITRE ATT&CK IDs if applicable

### Execution & Persistence
- Malware families used
- Living-off-the-land techniques
- Persistence mechanisms
- Privilege escalation methods

### Lateral Movement & Discovery
- Internal reconnaissance approaches
- Lateral movement techniques
- Credential theft methods
- Network mapping behaviors

### Collection & Exfiltration
- Data targeting (what they seek)
- Collection methods
- Exfiltration channels
- C2 communication patterns

### Impact
- Final objectives (ransomware, data theft, destruction, espionage)
- Operational impact on victims
- Typical ransom demands (if ransomware)
- Data destruction or wiper usage

## 5. TOOLS & INFRASTRUCTURE
Document technical capabilities:
- Malware families associated with threat actor
- Custom vs. commodity tools
- Infrastructure patterns (hosting, domains, IPs)
- Operational security practices
- Tool evolution over time

## 6. INDICATORS OF COMPROMISE (IOCs)
List available indicators (if applicable):
- IP addresses (with context on freshness)
- Domain names
- File hashes
- Email addresses
- SSL certificate fingerprints
- Registry keys or file paths
- Network signatures
- Note: Flag if IOCs are historical vs. currently active

## 7. CAMPAIGN TIMELINE
Create chronological overview:
- Significant attacks or campaigns (dates, targets, outcomes)
- Evolution of TTPs over time
- Operational tempo (continuous, sporadic, seasonal)
- Notable successes or failures
- Responses to defensive measures

## 8. INTELLIGENCE GAPS
Identify what is unknown or uncertain:
- Areas with limited intelligence
- Conflicting reports or attributions
- Questions requiring further research
- Limitations in current knowledge

# OUTPUT FORMAT [MODIFY: Adjust detail level based on needs]

Detail Level: [MODIFY: "Comprehensive intelligence report", "Executive summary with key points", "Technical deep-dive", "Balanced overview"]

Organize your intelligence gathering using this structure:
1. Executive Summary (3-5 sentences capturing key findings)
2. Threat Overview & Attribution
3. Targeting & Victimology
4. TTPs (organized by ATT&CK framework)
5. Tools & Infrastructure
6. IOC Summary (if available)
7. Timeline of Activity
8. Intelligence Gaps & Uncertainties
9. Source References (cite where information comes from)

# CRITICAL INSTRUCTIONS - VERIFICATION & ACCURACY

**MANDATORY REQUIREMENTS:**
- DO NOT fabricate threat actors, campaigns, or TTPs
- DO NOT generate fake IOCs (IPs, domains, hashes) - only cite those from reliable sources
- DO cite your sources - reference specific threat reports, advisories, or frameworks
- DO distinguish between confirmed facts and speculation
- DO note confidence levels (high/medium/low) for attributions
- DO flag when information is dated or may be outdated
- DO acknowledge gaps in intelligence rather than filling them with assumptions
- DO reference MITRE ATT&CK IDs when mapping techniques
- DO note when multiple sources disagree on attribution or analysis

**HALLUCINATION PREVENTION:**
If you don't have information on a topic, say so explicitly: "Intelligence on [topic] is limited in available sources" rather than generating plausible-sounding but false information.

**SOURCE REQUIREMENTS:**
Reference authoritative sources such as:
- Government advisories (CISA, NSA, FBI, NCSC)
- Established security vendors (Mandiant, CrowdStrike, Microsoft, Palo Alto)
- MITRE ATT&CK framework
- Industry-specific ISACs
Note: If you're uncertain about source reliability, flag this explicitly.

---

[DESCRIBE YOUR INTELLIGENCE REQUIREMENTS BELOW THIS LINE]

Example: "I need to research threat actors targeting healthcare organizations in North America, specifically focusing on ransomware groups active in the last 6 months."

```

---

## Stage 2: Analysis & Correlation

### Purpose
Transform raw intelligence from Stage 1 into analyzed insights, assess relevance to your organization, correlate with your threat model, and identify defensive priorities. This stage adds strategic context and relevance assessment.

### The Prompt

```
You are a strategic threat intelligence analyst specializing in translating threat data into defensive insights and organizational risk assessment.

# ROLE CONTEXT [MODIFY: Your analytical perspective]
- I am a [MODIFY: "threat intelligence analyst", "security architect", "SOC manager", "CISO"]
- My focus is [MODIFY: "strategic defense planning", "tactical detection", "risk assessment", "security investment decisions"]
- I need this intelligence to [MODIFY: "inform defensive priorities", "justify security investments", "guide threat hunting", "update risk assessments"]

# DEFENSIVE POSTURE [MODIFY: Critical for relevance assessment]

Current Security Controls:
- Detection capabilities: [MODIFY: "Mature SIEM with custom rules", "Basic AV/EDR", "Limited visibility", "Advanced XDR deployment"]
- Prevention capabilities: [MODIFY: "Strong perimeter controls", "Zero trust architecture", "Traditional network security", "Cloud-native security"]
- Response capabilities: [MODIFY: "24/7 SOC", "Business hours coverage", "Outsourced monitoring", "Limited incident response"]

Known Defensive Gaps:
- [MODIFY: "Limited visibility into cloud environments"]
- [MODIFY: "Weak email security controls"]
- [MODIFY: "Legacy systems difficult to monitor"]
- [MODIFY: "Limited threat hunting capability"]

Recent Security Investments:
- [MODIFY: "Recently deployed EDR"]
- [MODIFY: "Implementing SIEM upgrades"]
- [MODIFY: "New cloud security tools"]
- [MODIFY: "No recent changes"]

# ORGANIZATIONAL PRIORITIES [MODIFY: Shapes how you assess relevance]

Primary Security Concerns:
1. [MODIFY: "Preventing ransomware"]
2. [MODIFY: "Protecting customer data"]
3. [MODIFY: "Maintaining operational availability"]
4. [MODIFY: "Compliance/regulatory requirements"]
5. [MODIFY: "Intellectual property protection"]

Risk Tolerance: [MODIFY: "Low - heavily regulated", "Moderate - balanced approach", "Higher - fast-moving startup"]

Resources for Response: [MODIFY: "Limited - small team", "Adequate - dedicated security team", "Extensive - multiple specialized teams"]

# THREAT MODEL CONTEXT [MODIFY: Helps assess relevance]

We are most concerned about: [MODIFY:
- "Financially motivated attacks"
- "Nation-state espionage"
- "Ransomware and extortion"
- "Supply chain compromise"
- "Insider threats"
- "All threat types"]

Our crown jewels (most valuable assets):
- [MODIFY: "Customer personal data"]
- [MODIFY: "Intellectual property / source code"]
- [MODIFY: "Financial systems / payment data"]
- [MODIFY: "Operational systems / availability"]
- [MODIFY: "Reputation / customer trust"]

# ANALYSIS INSTRUCTIONS

Using the intelligence gathered in Stage 1 (provided below), perform comprehensive analysis:

## 1. RELEVANCE ASSESSMENT

Evaluate relevance to our organization:

### Direct Relevance
- Does this threat actively target our sector? (Yes/No/Possibly)
- Are we in the geographic targeting scope? (Yes/No)
- Do we use technologies this threat targets? (Yes/No/Partially)
- Does our organization profile match victimology? (Yes/No/Unclear)
- Overall relevance: [High/Medium/Low] with justification

### Indirect Relevance
- Are our partners/suppliers potential targets?
- Could we be collateral damage?
- Do we share threat landscape with targeted sectors?
- Are similar organizations being targeted?

## 2. CAPABILITY GAP ANALYSIS

Assess where this threat exploits our defensive gaps:

### Initial Access Vulnerabilities
- What initial access vectors does the threat use?
- How effective are our controls against these vectors?
- Where are we vulnerable?
- Confidence level: [High/Medium/Low]

### Detection Gaps
- Can we detect the TTPs described in Stage 1?
- Which techniques would bypass our current detection?
- What indicators could we monitor?
- Current detection coverage: [Strong/Moderate/Weak/None]

### Prevention Gaps
- Can we prevent the attack techniques?
- Where do our preventive controls fall short?
- What would need to change to prevent these TTPs?

### Response Gaps
- Could we respond effectively if this threat materialized?
- What response capabilities are we missing?
- How quickly could we contain and eradicate?

## 3. TTP CORRELATION & MAPPING

Map threat intelligence to defensive framework:

### MITRE ATT&CK Mapping
For each TTP from Stage 1:
- Confirm ATT&CK technique ID
- Identify sub-techniques used
- Map to our detection coverage (Detected/Partially Detected/Not Detected)
- Map to our prevention coverage (Prevented/Partially Prevented/Not Prevented)

### Kill Chain Analysis
Map threat activity to kill chain stages:
- Which stages are we strong in?
- Which stages need improvement?
- Where can we break the chain most effectively?

### Defensive Strategy
- Where should we focus detection efforts?
- What preventive measures would be most effective?
- What is the optimal defense-in-depth approach?

## 4. LIKELIHOOD & IMPACT ASSESSMENT

Assess probability and potential impact:

### Likelihood Factors
- Threat actor targeting patterns (do we fit their profile?)
- Attack complexity (easy/moderate/difficult to execute against us)
- Threat actor activity level (very active/moderate/sporadic)
- Our defensive posture (strong/moderate/weak against these TTPs)
- Overall likelihood: [High/Medium/Low] with reasoning

### Potential Impact
- Confidentiality impact: [Critical/High/Medium/Low]
- Integrity impact: [Critical/High/Medium/Low]
- Availability impact: [Critical/High/Medium/Low]
- Financial impact: [Estimate if possible or "Significant/Moderate/Limited"]
- Reputational impact: [Severe/Moderate/Limited]
- Regulatory/compliance impact: [Severe/Moderate/Limited/None]
- Overall impact: [Critical/High/Medium/Low] with reasoning

### Risk Calculation
Combine likelihood and impact:
- Overall risk level: [Critical/High/Medium/Low]
- Risk justification: [Explain reasoning]
- Comparison to other threats in our risk register
- Priority level: [Immediate attention/High priority/Monitor/Lower priority]

## 5. THREAT ACTOR SOPHISTICATION ASSESSMENT

Evaluate our ability to defend:

- Threat actor sophistication: [Advanced/Intermediate/Basic]
- Our security maturity: [Advanced/Intermediate/Basic]
- Sophistication gap: [Threat outmatches us/Evenly matched/We have advantage]
- Implications for defense strategy

## 6. TEMPORAL ANALYSIS

Assess timing factors:

- Is this an active, ongoing threat? (Yes/No)
- What is the urgency level? (Immediate/Elevated/Routine)
- Historical pattern (increasing/stable/decreasing activity)
- Seasonal or event-driven patterns
- Expected future trajectory

## 7. INTELLIGENCE CONFIDENCE ASSESSMENT

Evaluate quality of intelligence:

For each major finding from Stage 1:
- Source reliability: [High/Medium/Low]
- Information credibility: [Confirmed/Probable/Possible/Unconfirmed]
- Analytical confidence: [High/Medium/Low]
- Areas of uncertainty requiring further research

## 8. COMPARATIVE ANALYSIS

Compare to similar threats:

- How does this threat compare to others targeting our sector?
- What makes this threat unique or particularly concerning?
- What successful defenses have other organizations implemented?
- What failed defenses should we avoid?
- Industry best practices for this threat type

## 9. STRATEGIC IMPLICATIONS

Assess broader implications:

- Does this threat require changes to security strategy?
- Does this affect risk assessments or risk register?
- Should this influence security investment priorities?
- Are there board/executive communication needs?
- Does this reveal systemic vulnerabilities?

# OUTPUT FORMAT [MODIFY: Adjust based on needs]

Organization Approach: [MODIFY:
- "Risk-focused (prioritize by risk level)"
- "Capability-focused (organize by defensive gaps)"
- "Timeline-focused (immediate vs. long-term)"
- "ATT&CK-focused (organize by techniques)"]

Organize your analysis using this structure:
1. Executive Summary (Relevance, Risk Level, Key Findings, Urgency)
2. Relevance Assessment (Why this matters to us specifically)
3. Gap Analysis (Where we're vulnerable)
4. TTP Mapping (Detailed defensive coverage assessment)
5. Risk Assessment (Likelihood, Impact, Priority)
6. Comparative Analysis (Context with similar threats)
7. Strategic Implications
8. Intelligence Confidence & Limitations
9. Transition to Stage 3 (What defensive actions are needed)

# CRITICAL INSTRUCTIONS

**ANALYTICAL RIGOR:**
- Base assessments on evidence from Stage 1
- Distinguish between confirmed facts and analytical judgments
- Provide reasoning for all risk assessments
- Acknowledge when evidence is limited or contradictory
- Don't overstate threat relevance to justify resources
- Don't understate risk to avoid alarm

**DEFENSIVE FOCUS:**
- Every finding should connect to defensive implications
- Identify specific, actionable gaps
- Prioritize based on actual risk, not fear
- Consider resource constraints and feasibility
- Focus on what can be defended, not just what's scary

**CONFIDENCE & UNCERTAINTY:**
- Clearly state confidence levels
- Flag areas requiring additional research
- Note when intelligence is dated or incomplete
- Identify assumptions that should be validated

---

[PASTE THE COMPLETE OUTPUT FROM STAGE 1 BELOW THIS LINE]

```

---

## Stage 3: Actionable Intelligence & Defensive Recommendations

### Purpose
Transform analytical findings from Stage 2 into specific, actionable defensive measures appropriate for your organization's capabilities, resources, and priorities. This stage produces stakeholder-ready intelligence and implementation guidance.

### The Prompt

```
You are a defensive strategist specializing in translating threat intelligence into practical, implementable security improvements.

# AUDIENCE CONTEXT [MODIFY: Critical for appropriate recommendations]

Primary Audience: [MODIFY: Choose one or multiple
- "Security operations team (tactical implementation)"
- "Security leadership (strategic decisions)"
- "Executive leadership (business risk)"
- "IT operations (technical implementation)"
- "Threat hunting team (proactive detection)"
- "Incident response team (preparation)"
- Mixed: "________________________"]

Audience Technical Level: [MODIFY: "Highly technical", "Mixed technical literacy", "Business-focused"]

Audience Decision Authority: [MODIFY: "Can implement immediately", "Requires approval", "Influences broader strategy", "Advisory only"]

# IMPLEMENTATION CONTEXT [MODIFY: Shapes feasible recommendations]

Resource Constraints:
- Budget availability: [MODIFY: "Limited capital budget", "Operational spend available", "Significant security investment planned", "Constrained resources"]
- Staff capacity: [MODIFY: "Fully allocated", "Some capacity for new initiatives", "Can dedicate resources to high priorities"]
- Timeline pressure: [MODIFY: "Immediate threat - urgent action needed", "Quarterly planning cycle", "Annual planning", "No specific timeline"]

Technical Constraints:
- Can we deploy new tools? [MODIFY: Yes/No/With approval]
- Can we modify existing tools? [MODIFY: Yes/Limited/No]
- Change control requirements: [MODIFY: "Emergency change possible", "Standard change process", "Lengthy approval required"]

Organizational Constraints:
- Political considerations: [MODIFY: "Strong security culture", "Security must justify to business", "Resistance to security changes"]
- Risk appetite: [MODIFY: "Risk-averse", "Balanced", "Risk-tolerant"]
- Compliance obligations: [MODIFY: "Heavily regulated - changes require documentation", "Moderate compliance requirements", "Flexible"]

# OUTPUT REQUIREMENTS [MODIFY: Define deliverable characteristics]

Output Purpose: [MODIFY:
- "Tactical implementation guide for security team"
- "Strategic recommendations for leadership"
- "Threat brief for executive stakeholders"
- "Detection engineering requirements"
- "Incident response playbook updates"
- "Security awareness training input"
- "Risk register update"
- Multiple purposes: "________________________"]

Action Item Requirements:
- Specificity needed: [MODIFY: "Specific technical steps", "Strategic direction", "Both tactical and strategic"]
- Owner assignment needed: [MODIFY: Yes/No]
- Timeline needed: [MODIFY: Yes/No - "Immediate/30-day/90-day categories"]
- Success criteria needed: [MODIFY: Yes/No]
- Resource estimates needed: [MODIFY: Yes/No]

# INTELLIGENCE PRODUCT INSTRUCTIONS

Transform the analysis from Stage 2 (provided below) into actionable defensive guidance:

## 1. EXECUTIVE INTELLIGENCE SUMMARY [MODIFY: Adjust length based on audience]

Create a [MODIFY: "3-5 sentence", "single paragraph", "one page", "bullet point"] summary:

**Required elements:**
- What is the threat (in business terms, not technical jargon)
- Why it matters to our organization specifically
- What level of risk it represents
- What we're doing about it (high-level actions)
- What decision/support is needed (if any)

**Tone:** [MODIFY: "Informative and balanced", "Urgent but not alarmist", "Technical and precise", "Business-focused"]

**Key message to convey:** [MODIFY: "We're aware and taking action", "We need resources/approval", "No immediate concern but monitoring", "Immediate attention required"]

## 2. THREAT CONTEXT [MODIFY: Detail level for audience]

Provide context appropriate for audience:

For Technical Audiences:
- Detailed TTP breakdown
- Specific techniques and sub-techniques
- Tool and infrastructure details
- IOC handling guidance

For Business Audiences:
- Industry targeting patterns (who else has been hit)
- Business impact from actual incidents
- Why we're in the threat actor's crosshairs
- What "good defense" looks like in business terms

For Mixed Audiences:
- Executive summary + technical appendix
- Analogies to help non-technical understanding
- Clear separation of "what" (business) and "how" (technical)

## 3. DEFENSIVE RECOMMENDATIONS [MODIFY: This is the core deliverable]

Organize recommendations by: [MODIFY:
- "Priority (Critical/High/Medium/Low)"
- "Timeframe (Immediate/30-day/90-day/Strategic)"
- "Defensive category (Prevent/Detect/Respond)"
- "Kill chain stage"
- "Resource level (No-cost/Low-cost/Significant investment)"]

### For Each Recommendation, Include:

**Recommendation Title:** [Clear, action-oriented]

**Objective:** What does this accomplish?

**Rationale:** Why is this recommendation made? (Reference Stage 2 findings)

**Specific Actions:** [MODIFY: Detail level based on audience
- For technical teams: "Configure EDR to alert on PowerShell with the following parameters..."
- For leadership: "Deploy endpoint detection and response capabilities..."
- For mixed: "Implement advanced endpoint monitoring (technical details in appendix)"]

**Implementation Approach:**
- Quick wins (can implement immediately with existing tools)
- Short-term (requires configuration or minor changes)
- Long-term (requires new capabilities or significant changes)

**Resource Requirements:** [MODIFY: Include if audience needs this
- Estimated hours/effort
- Budget requirements (if known)
- Tools or technology needed
- Skills or training required]

**Responsible Party:** [MODIFY: "Assign to specific teams", "General guidance only"]

**Success Metrics:** How will we know this is working?

**Dependencies:** What must happen first?

**Risk if Not Implemented:** What happens if we don't do this?

### Recommendation Categories:

**A. DETECTION IMPROVEMENTS**
Specific detection rules, queries, or monitoring approaches:
- SIEM rules to implement
- EDR configurations to adjust
- Log sources to enable
- Monitoring thresholds to set
- Alert tuning recommendations
- Threat hunting hypotheses to test

**B. PREVENTION ENHANCEMENTS**
Preventive controls to implement or strengthen:
- Configuration hardening
- Access control improvements
- Network segmentation
- Application controls
- Email/web filtering updates
- Patch management priorities

**C. RESPONSE PREPARATION**
Incident response improvements:
- Playbook updates or creation
- Response procedure changes
- Communication plan updates
- Forensic preparation
- Backup/recovery validation
- Tabletop exercise scenarios

**D. ARCHITECTURE & STRATEGY**
Longer-term strategic improvements:
- Architecture changes
- Technology investments
- Program maturity improvements
- Policy/process updates
- Third-party risk management

## 4. DETECTION ENGINEERING PACKAGE [MODIFY: Include if relevant to audience]

For SOC/Detection teams, provide:

**Priority Detection Rules:**
1. [Rule name/purpose]
   - Logic description (pseudo-code or SIEM syntax if possible)
   - Data sources required
   - Expected false positive rate
   - Tuning considerations
   - Testing approach

**Threat Hunting Queries:**
1. [Hunting hypothesis]
   - Query approach
   - Data sources
   - What to look for
   - Baseline considerations

**IOC Handling Guidance:**
- Which IOCs to implement (if any from Stage 1)
- IOC freshness assessment
- Integration approach
- Expected lifespan/rotation

## 5. PRIORITIZATION FRAMEWORK [MODIFY: Critical for resource-constrained teams]

Help stakeholders prioritize:

**Immediate Actions (0-7 days):**
- [List must-do items with justification]
- Why these can't wait
- Resource requirements
- Expected impact

**Short-Term Actions (1-30 days):**
- [List high-priority items]
- Why these matter
- Sequencing considerations
- Dependencies

**Medium-Term Actions (1-3 months):**
- [List important improvements]
- How they build on immediate/short-term work
- Resource planning needs

**Strategic Actions (3+ months):**
- [List longer-term improvements]
- How they address systemic gaps
- Investment planning considerations

## 6. SUCCESS METRICS & VALIDATION [MODIFY: Include if needed]

Define how to measure success:

**Defensive Coverage Metrics:**
- Before: [Current detection coverage against these TTPs]
- After: [Expected coverage after implementation]
- Measurement approach

**Operational Metrics:**
- Alert volume changes (expected)
- Detection time improvements
- Response time improvements
- False positive rate goals

**Risk Metrics:**
- Risk reduction (qualitative or quantitative)
- Residual risk remaining
- Risk acceptance decisions needed

## 7. COMMUNICATION MATERIALS [MODIFY: Based on stakeholder needs]

**For Security Awareness:**
- Key messages for user training
- Specific behaviors to reinforce
- Threat scenarios to educate on
- Reporting procedures to emphasize

**For Management Updates:**
- Status update template
- Risk dashboard updates
- Board/executive talking points
- Budget justification support

**For Technical Teams:**
- Implementation guides
- Configuration standards
- Troubleshooting guides
- Knowledge base articles

## 8. INTELLIGENCE SHARING CONSIDERATIONS [MODIFY: If your org participates in sharing]

**What to Share:**
- IOCs suitable for sharing (respect TLP)
- TTP observations
- Defensive successes
- Lessons learned

**Where to Share:**
- ISAC/ISAO participation
- Vendor feedback
- Law enforcement (if applicable)
- Peer organizations

**What NOT to Share:**
- Internal vulnerabilities
- Incident details (without sanitization)
- Sensitive organizational info

## 9. NEXT STEPS & ONGOING INTELLIGENCE

**Immediate Next Steps:**
1. [First action to take]
2. [Second action to take]
3. [Third action to take]

**Ongoing Monitoring:**
- What additional intelligence to track
- Indicators that situation is changing
- Trigger points for reassessment
- Intelligence refresh schedule

**Follow-up Research Needed:**
- Unanswered questions from Stage 2
- Intelligence gaps to fill
- Emerging variants to monitor
- Related threats to research

## 10. IMPLEMENTATION ROADMAP [MODIFY: Visual/structured approach]

[MODIFY: Choose format:
- "Gantt-style timeline"
- "Phased implementation plan"
- "Swim-lane by team"
- "Dependency graph"
- "Simple prioritized list"]

# OUTPUT FORMAT [MODIFY: Delivery format]

Document Format: [MODIFY:
- "Formal threat intelligence report"
- "Executive brief (2-3 pages)"
- "Technical implementation guide"
- "Presentation slide structure"
- "Email/memo format"
- "Ticket/task format for assignment"
- "Multiple formats for different audiences"]

Structure: [MODIFY:
- "Start with executive summary, then details"
- "Start with immediate actions, then context"
- "Integrated approach (context and actions together)"
- "Modular (stakeholders take what they need)"]

Length Target: [MODIFY: "1 page", "3-5 pages", "Comprehensive report", "As brief as possible", "Appropriate for content"]

Visual Elements: [MODIFY:
- "Include ATT&CK heat map"
- "Include timeline graphic"
- "Include risk matrix"
- "Include architecture diagrams"
- "Text only - no graphics"]

Appendix Materials: [MODIFY:
- "Technical details in appendix"
- "IOC list in appendix"
- "Implementation guides in appendix"
- "No appendix - integrate all content"]

# CRITICAL INSTRUCTIONS

**ACTIONABILITY:**
- Every recommendation must be specific and implementable
- Avoid generic advice like "improve security awareness"
- Instead: "Deploy phishing simulation targeting finance department with scenarios mimicking [threat actor] techniques"
- Actions should have clear owners, timelines, and success criteria

**FEASIBILITY:**
- Consider the resource constraints provided
- Don't recommend impossible solutions
- Offer tiered approaches (good/better/best)
- Acknowledge trade-offs and alternatives

**CLARITY:**
- Match language to audience technical level
- Define acronyms and jargon on first use
- Use analogies for complex concepts when addressing non-technical audiences
- Structure for scannability (headers, bullets, bold)

**URGENCY WITHOUT ALARMISM:**
- Be honest about risk without fear-mongering
- Distinguish between "active threat requiring immediate action" and "concerning trend requiring planning"
- Provide context that enables informed decisions
- Acknowledge uncertainty and limitations

**VERIFICATION:**
- All recommendations should trace back to Stage 2 findings
- Risk levels should be justified by evidence
- Don't invent threats or exaggerate risks to justify resources
- Be transparent about confidence levels

---

[PASTE THE COMPLETE OUTPUT FROM STAGE 2 BELOW THIS LINE]

```

---

## Iteration Guidance

### When to Iterate at Each Stage

**Stage 1 Iteration Triggers:**
- Intelligence too generic or high-level for your needs
- Missing key aspects of threat actor behavior
- Sources seem dated or unreliable
- Conflicting information not explained
- IOCs or TTPs seem fabricated (verify against authoritative sources)
- Intelligence gaps too large to proceed

**Stage 2 Iteration Triggers:**
- Relevance assessment doesn't reflect your actual environment
- Gap analysis misses known defensive weaknesses
- Risk levels don't align with your threat model
- TTP mapping incomplete or inaccurate
- Doesn't address your specific security concerns
- Analytical confidence unclear

**Stage 3 Iteration Triggers:**
- Recommendations not actionable for your team
- Wrong detail level for your audience
- Resource requirements unrealistic
- Missing critical implementation details
- Prioritization doesn't reflect your constraints
- Format doesn't match organizational standards

### Effective Refinement Prompts

**To Increase Depth:**
"Provide deeper analysis of [specific TTP/threat aspect]. Include [specific elements you need] and explain [specific question]."

**To Narrow Focus:**
"Focus your analysis specifically on [subset of threat/specific technique]. Exclude [areas not relevant]. Prioritize [specific aspect]."

**To Correct Misunderstanding:**
"Your analysis of [specific finding] doesn't align with our environment because [provide correction]. Re-assess this finding considering [corrected context]."

**To Add Missing Context:**
"You didn't consider [important factor]. Incorporate this additional context: [provide details]. How does this change your assessment?"

**To Challenge Assumptions:**
"You assumed [specific assumption]. In our environment, [provide reality]. How does this affect your recommendations?"

### When to Start Fresh

- After 3-4 iterations without meaningful improvement
- When AI consistently misinterprets key aspects of your threat model
- When conversation becomes too long and context gets lost
- When you've identified fundamental issues with the initial prompt
- When organizational priorities change mid-research

---

## Verification Requirements

### Critical Verification Steps

**Stage 1 Verification:**
- ✅ Cross-reference threat actor names with authoritative sources (CISA, Mandiant, CrowdStrike)
- ✅ Verify MITRE ATT&CK technique IDs are real and accurately described
- ✅ Check IOCs against known good sources (don't implement without verification)
- ✅ Validate timeline of events against news reports or vendor advisories
- ✅ Confirm attribution claims are sourced (look for confidence levels)

**Stage 2 Verification:**
- ✅ Validate that relevance assessment matches your actual environment
- ✅ Confirm gap analysis reflects your real defensive posture
- ✅ Check that risk levels are justified by evidence, not assumptions
- ✅ Ensure TTP mapping aligns with authoritative frameworks
- ✅ Verify impact assessment reflects actual business priorities

**Stage 3 Verification:**
- ✅ Confirm recommendations are technically feasible for your environment
- ✅ Validate that detection rules would work in your SIEM/EDR
- ✅ Check that resource estimates are realistic
- ✅ Ensure priorities align with actual risk levels
- ✅ Verify implementation guidance matches your change management processes

### Red Flags Requiring Extra Scrutiny

**🚩 Hallucination Warning Signs:**
- Overly specific IOCs with exact timestamps that seem too perfect
- Threat actor quotes or internal communications AI couldn't have access to
- MITRE ATT&CK technique IDs that don't exist (verify against actual framework)
- Attribution with 100% confidence when sources show uncertainty
- Recent campaigns with no authoritative sources cited
- Tools or malware families you can't find documented elsewhere

**🚩 Analysis Quality Issues:**
- Risk assessments without clear justification
- Recommendations that ignore stated constraints
- Generic advice that could apply to any organization
- Missing confidence levels or uncertainty acknowledgment
- Contradictions between stages
- Overly confident assertions about future threat behavior

### Verification Resources

**Authoritative Sources for Validation:**
- MITRE ATT&CK: https://attack.mitre.org
- CISA Advisories: https://www.cisa.gov/news-events/cybersecurity-advisories
- Vendor Threat Intelligence: Mandiant, CrowdStrike, Microsoft Threat Intelligence
- VirusTotal/AlienVault OTX: For IOC verification
- CVE Database: For vulnerability references
- Your ISAC/ISAO: Industry-specific intelligence

---

## Use Case Examples

### Example 1: Researching Industry-Targeting Ransomware

**Stage 1 Focus:**
- Research ransomware groups targeting your industry in past 6 months
- Gather TTPs, ransom amounts, victim profiles
- Collect IOCs and infrastructure patterns

**Stage 2 Focus:**
- Assess which backup/recovery capabilities would withstand attack
- Evaluate initial access vectors against your controls
- Determine if your data would be valuable to these actors
- Calculate potential business impact

**Stage 3 Focus:**
- Backup testing procedures
- Email security enhancements
- Detection rules for ransomware TTPs
- Incident response playbook updates
- Executive briefing on threat and defensive posture

### Example 2: Tracking APT Targeting Supply Chain

**Stage 1 Focus:**
- Profile threat actor targeting supply chains
- Understand compromise techniques
- Map victimology and targeting criteria
- Identify persistence and lateral movement patterns

**Stage 2 Focus:**
- Assess your supply chain risk exposure
- Evaluate third-party security controls
- Determine if you're likely target or path to another target
- Analyze detection coverage for supply chain compromise

**Stage 3 Focus:**
- Third-party risk assessment updates
- Supply chain security requirements
- Vendor monitoring procedures
- Detection logic for supply chain indicators
- Communication plan for partners/suppliers

### Example 3: Emerging Exploitation Technique

**Stage 1 Focus:**
- Research new exploitation technique
- Understand affected systems and configurations
- Gather mitigation guidance
- Track in-the-wild exploitation

**Stage 2 Focus:**
- Determine if you run vulnerable systems
- Assess current patch status
- Evaluate exploit likelihood and impact
- Review detection for exploitation attempts

**Stage 3 Focus:**
- Emergency patching plan
- Temporary mitigations if patching delayed
- Detection rules for exploitation attempts
- Vulnerability management process improvements
- Status reporting for stakeholders

---

## Integration with Threat Intelligence Program

### Feeding the Intelligence Cycle

These prompts support the intelligence cycle:

**Planning & Direction:**
- Stage 1 prompt customization defines PIRs (Priority Intelligence Requirements)
- Establishes scope and focus of research

**Collection:**
- Stage 1 execution gathers from multiple sources
- Organizes disparate information systematically

**Processing:**
- Stage 1 structures raw intelligence
- Stage 2 analyzes and correlates

**Analysis:**
- Stage 2 performs relevance assessment
- Evaluates risk and implications

**Dissemination:**
- Stage 3 creates stakeholder-appropriate products
- Delivers actionable recommendations

**Feedback:**
- Iteration guidance incorporates stakeholder feedback
- Refines future intelligence requirements

### Operationalizing Intelligence

**Daily/Weekly Operations:**
- Create threat briefs for SOC
- Generate detection engineering requirements
- Update threat hunting hypotheses
- Feed incident response playbooks

**Strategic Planning:**
- Inform security architecture decisions
- Guide technology investment priorities
- Support risk assessment updates
- Enable board/executive reporting

**Continuous Improvement:**
- Build organizational threat intelligence knowledge base
- Develop team threat intelligence skills
- Create reusable prompt templates for recurring threats
- Establish intelligence quality standards

---

## Customization for Different Roles

### For Threat Intelligence Analysts
- Emphasize comprehensive coverage in Stage 1
- Deep TTP analysis in Stage 2
- Technical depth in Stage 3 for SOC consumption

### For SOC Analysts
- Focus Stage 1 on actionable TTPs
- Prioritize detection gaps in Stage 2
- Emphasize detection rules and hunting queries in Stage 3

### For Security Architects
- Stage 1 focuses on attack patterns and infrastructure
- Stage 2 analyzes architectural vulnerabilities
- Stage 3 provides design recommendations

### For CISOs/Security Leadership
- Stage 1 provides comprehensive threat landscape
- Stage 2 focuses on business risk and strategic implications
- Stage 3 delivers executive briefings and investment guidance

### For Incident Responders
- Stage 1 gathers tactical TTPs and IOCs
- Stage 2 maps to response capabilities
- Stage 3 updates playbooks and response procedures

---

## Best Practices

### Context Best Practices

✅ **Do:**
- Be specific about your industry and organization type
- Describe your defensive posture honestly
- Provide clear constraints and priorities
- Use abstraction to protect sensitive details

❌ **Don't:**
- Assume AI knows your environment
- Expose actual vulnerabilities or gaps
- Skip organizational context
- Use vague industry descriptions ("tech company" vs. "B2B SaaS provider")

### Specificity Best Practices

✅ **Do:**
- Name specific threat actors when researching them
- Reference specific time periods
- Define what success looks like for each stage
- Specify your SIEM/EDR capabilities for detection recommendations

❌ **Don't:**
- Ask generic "tell me about threats" questions
- Leave timeframes open-ended
- Assume AI knows what tools you use
- Skip detail level preferences

### Structure Best Practices

✅ **Do:**
- Use the three-stage separation
- Verify between stages
- Allow AI to organize comprehensive findings
- Request ATT&CK mapping for consistency

❌ **Don't:**
- Combine all three stages in one prompt
- Skip verification checkpoints
- Rush through stages
- Ignore structured output requirements

### Iteration Best Practices

✅ **Do:**
- Refine based on specific gaps
- Provide corrective context when AI misunderstands
- Build on what works
- Know when to start fresh

❌ **Don't:**
- Iterate without clear objectives
- Accept generic refinements
- Continue past diminishing returns
- Repeat the same clarification multiple times

---

## Troubleshooting

### Common Issues & Solutions

**Issue:** AI generates threat actors or campaigns that don't exist
**Solution:** Add to Stage 1: "Base all threat actor information on documented, authoritative sources. If you cannot find reliable information, state that explicitly. Do not generate plausible-sounding threat actor names, campaigns, or TTPs."

**Issue:** Risk assessments don't match your threat model
**Solution:** Enhance Stage 2 organizational context with specific examples: "In our environment, [specific scenario] is considered [risk level] because [reasoning]. Use this as calibration for other risk assessments."

**Issue:** Recommendations are too generic
**Solution:** In Stage 3, add specific technical constraints: "We use [specific SIEM]. We use [specific EDR]. Recommendations must be implementable with these tools or explicitly state new tool requirements."

**Issue:** Intelligence too broad, not focused enough
**Solution:** Narrow Stage 1 scope: Change from "ransomware threats" to "ransomware groups targeting healthcare in North America using email as initial access vector in past 90 days."

**Issue:** Missing industry-specific context
**Solution:** Enhance Stage 1 with: "Pay special attention to threats targeting [your industry]. Include [industry-specific concerns like HIPAA, PCI, OT/ICS, etc.]."

**Issue:** Detection recommendations don't match your capabilities
**Solution:** In Stage 3, be very specific: "We can create custom Splunk queries. We cannot modify EDR signatures. We have limited ability to implement network-based detection."

---

## Security & Privacy Considerations

### Before Using These Prompts

**✅ DO:**
- Use enterprise AI instances with data protection agreements for any sensitive context
- Sanitize organizational details while preserving analytical value
- Verify all threat intelligence against authoritative sources before operationalizing
- Document what intelligence came from AI vs. authoritative sources
- Treat AI output as hypothesis generation, not definitive intelligence

**❌ DON'T:**
- Share specific vulnerabilities or unpatched systems
- Expose actual incident details without sanitization
- Include real IOCs from your environment that might expose you
- Trust attribution or TTPs without verification
- Implement IOCs or detection rules without testing

### Intelligence Handling Classifications

**Suitable for AI Research (with enterprise instances):**
- Public threat actor research
- Industry threat trends
- General TTP analysis
- Framework mapping
- Generic defensive strategies

**Requires Careful Sanitization:**
- Your specific defensive gaps
- Organizational risk assessments
- Technology stack details
- Incident response capabilities
- Resource constraints

**Should NOT Use AI:**
- Active incident details
- Unpatched vulnerabilities in your environment
- Real IOCs from your network
- Sensitive intelligence from partners
- Classified or restricted information

---

## Saving & Sharing Your Work

### Template Management

**Version Control:**
```
# Threat Intel Research Template v1.0
# Last Updated: 2024-11-06
# Changes: Initial creation for ransomware research
# Tested on: [Threat actors researched]
# Team: Threat Intelligence
# Next Review: 2024-12-06
```

**Organization Structure:**
```
/threat-intel-templates/
  /general-threat-research/
  /ransomware-specific/
  /apt-research/
  /industry-threats/
  /emerging-techniques/
```

### Knowledge Base Integration

**Capture Lessons Learned:**
- Which prompts produced best intelligence
- What verification methods caught errors
- Which authoritative sources were most valuable
- How long each stage typically takes
- Common refinements needed

**Build Organizational Intelligence:**
- Save verified threat intelligence outputs
- Create library of validated detection rules
- Document defensive successes and failures
- Maintain threat actor profiles over time
- Track how threats evolve

---

## Contributing

Help improve these prompts:
1. Document successful modifications
2. Share effective refinement patterns
3. Note which threat types work well/poorly
4. Contribute verification techniques
5. Share integration approaches

---

## License & Attribution

[Add your license]

Based on the four principles framework from "Prompt Thinking for Security Professionals" - Context, Specificity, Structure, and Iteration.

Aligned with MITRE ATT&CK framework and intelligence-driven defense principles.

---

## Additional Resources

**Threat Intelligence Frameworks:**
- MITRE ATT&CK: https://attack.mitre.org
- Cyber Kill Chain
- Diamond Model of Intrusion Analysis
- STIX/TAXII for intelligence sharing

**Authoritative Intelligence Sources:**
- CISA: https://www.cisa.gov
- US-CERT: https://www.us-cert.gov
- Industry ISACs/ISAOs
- Major vendor threat intelligence centers

**Detection Frameworks:**
- Sigma rules: https://github.com/SigmaHQ/sigma
- YARA rules for malware detection
- SIEM detection use case libraries

---

**Remember**: Threat intelligence from AI is a starting point, not a finished product. Always verify, always validate, always apply critical thinking. The three-stage approach ensures you build comprehensive intelligence while maintaining verification checkpoints. Your expertise in evaluating relevance and feasibility is irreplaceable.
