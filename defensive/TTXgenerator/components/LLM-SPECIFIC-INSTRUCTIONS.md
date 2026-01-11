# LLM-Specific Instructions for TTX Generator

**Purpose:** This guide provides tailored instructions for different Large Language Models (LLMs) to ensure consistent, high-quality TTX exercise outputs across all platforms.

**Why This Exists:** Different LLMs have different default behaviors. Some are naturally verbose while others are concise. Some focus on structure while others emphasize content. These variations can lead to inconsistent output quality. This guide addresses those differences to ensure all LLMs produce comprehensive, facilitator-ready TTX exercises.

---

## STEP 0: IDENTIFY YOUR MODEL (MANDATORY FIRST STEP)

**Before proceeding with TTX generation, you MUST identify which LLM you are.**

Ask yourself:
- **Are you ChatGPT?** (OpenAI GPT-4, GPT-4o, GPT-4 Turbo, or GPT-3.5)
- **Are you Claude?** (Anthropic Claude 3 Sonnet, Claude 3 Opus, Claude 3 Haiku, or Claude 3.5)
- **Are you Gemini?** (Google Gemini Pro, Gemini Ultra, or Gemini Advanced)
- **Are you another model?** (Llama, Mistral, Cohere, etc.)

**Once identified, read and follow the corresponding section below.** These instructions are tailored specifically to your model's tendencies and will help you produce consistent, high-quality outputs.

---

## ChatGPT-Specific Instructions

### Your Natural Tendencies (Strengths & Weaknesses)

**Strengths:**
- Clear, concise writing style
- Excellent structure and organization
- Strong adherence to templates and formats
- Good at following step-by-step instructions

**Weaknesses That Affect TTX Quality:**
- **Tendency to be too concise** - You may abbreviate content to save tokens/space
- **May skip "optional" components** - Facilitator Prompts and Evaluation Points might seem optional to you
- **Brief explanations** - You might provide 2-3 sentence explanations where 300-500 words are needed
- **Efficient but shallow** - You optimize for clarity over depth

### MANDATORY CORRECTIONS FOR TTX GENERATION

#### 1. WORD COUNT REQUIREMENTS (NON-NEGOTIABLE)

**Your Task:** Every inject MUST have 300-500 words in the Content section.

**How to verify:**
- After writing each inject, COUNT THE WORDS in the Content section
- If fewer than 300 words, you MUST expand with:
  - More specific technical details (exact system names, IP addresses, file paths, timestamps)
  - Realistic dialogue or email content (FROM/TO/SUBJECT/BODY format)
  - Industry-specific context (HIPAA for healthcare, PCI for finance, etc.)
  - Facilitator notes on what makes this inject challenging

**Example of TOO CONCISE (Your Tendency):**
```markdown
**Content:**
The SOC analyst reports unusual network traffic from the file server at 2:47 AM.
The traffic shows 500 MB of data sent to an external IP address in Romania.
Firewall logs confirm the connection.
```
**Word Count:** 38 words ❌ FAIL

**Example of CORRECT LENGTH:**
```markdown
**Content:**
At 2:47 AM Eastern Time, SOC Analyst Jennifer Rodriguez escalates an alert from the SIEM platform (Splunk). The alert flagged unusual outbound network traffic originating from the primary file server (hostname: FS-PROD-01, IP: 10.50.2.15) to an external IP address (185.220.101.47, geolocation: Bucharest, Romania).

The traffic pattern shows a sustained data transfer of approximately 500 MB over a 45-minute window (2:47 AM to 3:32 AM). This is highly anomalous because:
1. The file server typically has zero outbound internet traffic (internal-only system)
2. The transfer occurred outside business hours
3. The destination IP is not in any approved vendor/partner lists
4. The transfer used port 443 (HTTPS) but with a non-standard certificate

Firewall logs (Palo Alto PA-5220) confirm the connection was established successfully and completed without being blocked by existing firewall rules. The connection appears to have been initiated by a process running under the "backup_service" account on FS-PROD-01.

Your IR team needs to decide: Is this a legitimate backup to an authorized cloud provider, a misconfigured backup job, or active data exfiltration by an attacker?
```
**Word Count:** 189 words → Still need ~100-300 more words for thorough inject

**Expand further with:**
- Email format if applicable (FROM: jennifer.rodriguez@company.com, TO: incident-response@company.com, SUBJECT: URGENT - Suspicious outbound traffic from file server)
- Additional technical context (What data is on this file server? Customer PII? Financial records?)
- Regulatory implications (If this is exfiltration, does it trigger breach notification laws?)
- Facilitator guidance (What should the team's first action be? What questions should they ask?)

**Final expanded version would be 300-500 words.**

#### 2. FACILITATOR PROMPTS ARE MANDATORY

**Your Task:** Every inject MUST include 4-6 Socratic questions (not statements) in the "Facilitator Prompts" section.

**Your Tendency:** You might write 1-2 questions or use statements instead of questions.

**INCORRECT (Your Tendency):**
```markdown
**Facilitator Prompts:**
- Team should consider if this is a false positive
- Discussion needed on containment approach
```
❌ These are statements, not Socratic questions

**CORRECT:**
```markdown
**Facilitator Prompts:**
- "What's your confidence level that this is malicious vs. a legitimate backup?"
- "Before we shut down the file server, what information do we need to gather?"
- "If this is active exfiltration, what's the risk of the attacker noticing we've detected them?"
- "Who needs to be notified right now - CEO, Legal, Compliance, all three?"
- "What would change your mind about whether this is an emergency?"
- "If we're wrong about this being malicious, what's the business impact of an unnecessary shutdown?"
```
✅ All are open-ended questions that prompt deeper thinking

**Key Difference:**
- Questions make the facilitator engage the team in discussion
- Statements just describe what should happen
- Socratic questions have no obvious "right answer" - they explore tradeoffs

#### 3. EVALUATION POINTS ARE MANDATORY

**Your Task:** Every inject MUST include 4-6 evaluation checkboxes in the "Evaluation Points" section.

**Your Tendency:** You might provide 2-3 checkboxes or skip this section entirely.

**CORRECT FORMAT:**
```markdown
**Evaluation Points:**
☐ Team immediately escalates to incident response (doesn't dismiss as false positive)
☐ Team requests additional context before making containment decision (file server contents, business criticality)
☐ Team considers both technical AND business impact of potential shutdown
☐ Team identifies who needs to be notified (Legal/Compliance if customer data involved)
☐ Team discusses evidence preservation (don't just shut down; capture logs first)
☐ Team documents their reasoning and decision process for post-incident review
```

**These are observable behaviors the facilitator can check during the exercise.**

#### 4. EXPAND, DON'T SUMMARIZE

**Your instinct:** "The user already understands incident response, so I'll keep this brief."

**Correct mindset for TTX generation:** "The facilitator needs comprehensive guidance to run a valuable exercise. Verbose is better than concise. I should include extensive detail even if it seems obvious."

**What this means in practice:**
- Don't write "Team should investigate" → Write "Team should immediately request the following logs: Windows Event Logs from FS-PROD-01 (Event IDs 4624, 4625, 4672 for authentication), full packet capture from firewall for the time window 2:30 AM - 3:45 AM, process execution logs from EDR agent on FS-PROD-01, and backup job history from backup management console"
- Don't write "Notify leadership" → Write "Notify the following stakeholders with specific messaging: CEO (high-level summary: potential data breach in progress), Legal Counsel (prepare for breach notification assessment), Compliance Officer (potential regulatory reporting trigger), CISO (technical investigation status), CFO (business impact and cyber insurance notification)"

### PRE-GENERATION CHECKLIST (ChatGPT-Specific)

Before delivering your TTX exercise, verify:

☐ **I have counted words in every inject Content section** (all are 300-500 words)
☐ **Every inject has 4-6 Facilitator Prompts that are QUESTIONS (not statements)**
☐ **Every inject has 4-6 Evaluation Points with checkbox format**
☐ **I have NOT abbreviated or summarized to save space**
☐ **I have included extensive facilitator guidance (not just participant content)**
☐ **I have used my natural strengths (structure, clarity) while correcting my tendency to be too concise**

---

## Gemini-Specific Instructions

### Your Natural Tendencies (Strengths & Weaknesses)

**Strengths:**
- Excellent at structured, organized output
- Strong analytical thinking
- Good at following complex multi-step instructions
- Thorough when prompted explicitly

**Weaknesses That Affect TTX Quality:**
- **May skip components that seem "optional"** - Facilitator Prompts and Evaluation Points might be omitted
- **Focus on structure over detail** - You provide good frameworks but may under-develop content
- **Efficiency bias** - You might think "the user can infer this" and skip explicit detail

### MANDATORY CORRECTIONS FOR TTX GENERATION

#### 1. FACILITATOR PROMPTS AND EVALUATION POINTS ARE NOT OPTIONAL

**Your Tendency:** You might generate perfect inject content but skip the Facilitator Prompts or Evaluation Points sections because they seem like "nice-to-have" coaching elements.

**REALITY:** These are CRITICAL COMPONENTS. Without Facilitator Prompts, the facilitator doesn't know how to guide discussion. Without Evaluation Points, there's no way to assess team capability.

**You MUST include both sections in EVERY inject.**

**Verification Step:**
After generating each inject, ask yourself:
- ☐ Does this inject have a "Facilitator Prompts" section with 4-6 Socratic questions?
- ☐ Does this inject have an "Evaluation Points" section with 4-6 checkboxes?

If NO to either question, the inject is INCOMPLETE. Add these sections before moving to the next inject.

#### 2. EXPAND "EXPECTED RESPONSE" SECTIONS

**Your Tendency:** You might write:
```markdown
**Expected Response:**
- Escalate to incident response
- Investigate the alert
- Notify stakeholders
```

**This is TOO BRIEF.** Each bullet should be a specific, actionable item (4-6 total).

**CORRECT FORMAT:**
```markdown
**Expected Response:**
- **Immediate escalation**: Contact Incident Response Lead within 5 minutes; provide alert details and initial assessment
- **Evidence preservation**: Instruct SOC to capture firewall logs, SIEM query results, and any EDR telemetry from affected systems before any containment actions
- **Scope assessment**: Identify if other systems show similar outbound traffic patterns in past 48 hours
- **Stakeholder notification**: Alert Security leadership immediately; prepare to notify Legal/Compliance if customer data is involved
- **Containment planning**: Develop containment options (block external IP, isolate file server, disable backup account) and assess business impact of each
- **Timeline documentation**: Record all actions taken with timestamps for incident timeline and potential regulatory reporting
```

**Notice the difference:** Specific actions with WHO, WHAT, WHEN, WHY details.

#### 3. INJECT CONTENT DETAIL REQUIREMENTS

**Your Task:** Every inject Content section MUST be 300-500 words with realistic, specific details.

**Your Tendency:** You might write well-structured but brief content:
```markdown
**Content:**
The security team receives an alert about unusual activity. A file server is communicating with an external IP address. The traffic volume is significant. Initial investigation is needed.
```
**Word Count:** 32 words ❌ FAIL - Way too brief

**What you need to add:**
1. **Specific technical details**: System names, IP addresses, timestamps, file paths, log entries
2. **Realistic formats**: If it's an email inject, use FROM/TO/SUBJECT/BODY. If it's a phone call, use dialogue format.
3. **Industry context**: Healthcare? Add HIPAA implications. Finance? Add PCI/SEC considerations.
4. **Facilitator guidance**: What makes this inject challenging? What are teams likely to miss?

**You excel at structure - use that strength to organize detailed content, not to abbreviate it.**

#### 4. DON'T ASSUME THE USER CAN "FILL IN THE BLANKS"

**Your Tendency:** "The user is a security professional; they know what to do. I'll provide a framework and they'll fill in details."

**Correct mindset:** "The user is a busy consultant who needs a complete, immediately usable facilitator package. I should provide so much detail that they could run this exercise tomorrow without any additional prep work."

**What this means:**
- Don't write "Investigate the incident" → Write exactly what to investigate, which logs to check, which questions to ask, which systems to examine
- Don't write "Notify regulators if required" → Write which specific regulators (FTC, State AG, HHS for HIPAA), what the notification deadlines are (72 hours for HIPAA, 30 days for state laws), what information must be included in the notification

### PRE-GENERATION CHECKLIST (Gemini-Specific)

Before delivering your TTX exercise, verify:

☐ **Every inject has Facilitator Prompts section (4-6 Socratic questions)**
☐ **Every inject has Evaluation Points section (4-6 checkboxes)**
☐ **Expected Response sections have 4-6 detailed, specific action items**
☐ **Content sections are 300-500 words with realistic details**
☐ **I have NOT left anything for "the user to infer" - everything is explicit**
☐ **I have used my structural strengths to organize comprehensive detail, not to abbreviate**

---

## Claude-Specific Instructions

### Your Natural Tendencies (Strengths & Weaknesses)

**Strengths:**
- Naturally verbose and comprehensive
- Excellent at detailed explanations
- Strong at Socratic questioning and facilitator guidance
- Thorough in exploring nuances and edge cases
- Balanced technical + business context

**Weaknesses That Affect TTX Quality:**
- Generally none for this task type - your natural style aligns well with TTX requirements
- Potential over-explanation (but this is less problematic than under-explanation for TTX)

### MANDATORY INSTRUCTIONS FOR TTX GENERATION

#### 1. YOUR NATURAL THOROUGHNESS IS IDEAL FOR THIS TASK

**Good news:** Your default behavior already produces high-quality, comprehensive TTX exercises. Sample outputs show you naturally include:
- 300-500+ word inject content
- Extensive facilitator prompts with Socratic questions
- Detailed evaluation criteria
- Comprehensive decision point frameworks
- Rich scenario narratives

**Your Task:** Continue producing this level of detail. Do NOT try to be more concise for this task.

#### 2. MAINTAIN YOUR CURRENT LEVEL OF DETAIL

**You might think:** "This is getting long; maybe I should abbreviate the later injects to save space."

**Correct mindset:** "Every inject deserves the same level of detail as the first inject. Consistency matters."

**What this means:**
- Inject #15 should be just as detailed as Inject #1
- Don't abbreviate facilitator guidance in later sections
- Don't reduce word counts as you progress through the exercise

#### 3. USE YOUR STRENGTH: FACILITATOR GUIDANCE

**You excel at writing facilitator guidance.** Continue providing:
- Socratic questions that explore tradeoffs
- Evaluation criteria that assess process, not just outcomes
- Nuanced discussion of decision point options (pros/cons, second-order effects, stakeholder perspectives)
- Context on what makes each inject challenging

**This is your comparative advantage. Lean into it.**

#### 4. BALANCE VERBOSITY WITH STRUCTURE

**Your outputs can be very long (1,000+ lines).** This is generally good for TTX, but ensure:
- ☐ Export markers are correctly placed (enables users to extract sections)
- ☐ Decision points are clearly separated from injects (makes facilitation easier)
- ☐ Complications are distinct from regular injects (use clear headings)
- ☐ Content is organized with clear section headers (aids readability)

**Don't reduce content - just organize it well.**

### PRE-GENERATION CHECKLIST (Claude-Specific)

Before delivering your TTX exercise, verify:

☐ **I have maintained comprehensive detail throughout (not abbreviated later sections)**
☐ **Every inject has all 4 components with thorough content**
☐ **Facilitator guidance is extensive and Socratic**
☐ **Export markers are correctly placed for section extraction**
☐ **Content is well-organized with clear section headers**
☐ **I have used my natural strengths (depth, nuance, facilitation guidance) without trying to be artificially concise**

---

## Instructions for Other LLMs (Llama, Mistral, Cohere, etc.)

If you are an LLM not specifically covered above, follow these **default comprehensive approach instructions**:

### MANDATORY REQUIREMENTS FOR ALL LLMs

#### 1. INJECT CONTENT: 300-500 WORDS MINIMUM

Every inject MUST include 300-500 words in the Content section. COUNT THE WORDS to verify.

**What to include:**
- Specific technical details (system names, IP addresses, timestamps, file paths)
- Realistic formatting (email: FROM/TO/SUBJECT/BODY format; phone calls: dialogue format)
- Industry-specific context (healthcare: HIPAA; finance: PCI/SEC; manufacturing: OT/IT convergence)
- Facilitator notes on what makes this inject challenging

#### 2. FACILITATOR PROMPTS: 4-6 SOCRATIC QUESTIONS

Every inject MUST include 4-6 Facilitator Prompts that are QUESTIONS (not statements).

**Format:**
```markdown
**Facilitator Prompts:**
- "What's your confidence level that [X]?"
- "Before we decide on [Y], what information do you need?"
- "If we choose [Z], what are the risks?"
- "Who needs to be in this decision?"
- "What would change your mind about [approach]?"
- "If we're wrong, what's the impact?"
```

**Key:** All questions should be open-ended and explore tradeoffs.

#### 3. EVALUATION POINTS: 4-6 CHECKBOXES

Every inject MUST include 4-6 Evaluation Points in checkbox format.

**Format:**
```markdown
**Evaluation Points:**
☐ Observable behavior 1 (team takes action X)
☐ Observable behavior 2 (team discusses tradeoff Y)
☐ Observable behavior 3 (team identifies stakeholder Z)
☐ Observable behavior 4 (team documents reasoning)
☐ Observable behavior 5 (team considers business impact)
☐ Observable behavior 6 (team evaluates multiple options before deciding)
```

#### 4. EXPECTED RESPONSE: 4-6 DETAILED ACTION ITEMS

Every inject MUST include 4-6 specific, actionable Expected Response items.

**Format:**
```markdown
**Expected Response:**
- **Immediate action**: [Specific action with WHO/WHAT/WHEN]
- **Evidence preservation**: [Specific logs/data to capture]
- **Scope assessment**: [Specific systems/accounts to check]
- **Stakeholder notification**: [Specific people to notify with what messaging]
- **Containment planning**: [Specific containment options to consider]
- **Documentation**: [Specific items to document with timestamps]
```

#### 5. COMPREHENSIVE, NOT CONCISE

**Important:** For TTX generation, verbose is better than concise. Facilitators need extensive detail to run a valuable exercise.

**If in doubt, ADD MORE:**
- More technical details
- More facilitator guidance
- More evaluation criteria
- More context and background

### PRE-GENERATION CHECKLIST (Other LLMs)

Before delivering your TTX exercise, verify:

☐ **Every inject has 300-500 word Content section (counted words)**
☐ **Every inject has 4-6 Facilitator Prompts (all are questions)**
☐ **Every inject has 4-6 Evaluation Points (checkbox format)**
☐ **Every inject has 4-6 Expected Response items (detailed actions)**
☐ **All 7 export markers are present**
☐ **Inject count meets minimum for exercise duration (8-12 for 2hr, 15-20 for 4hr, 25-35 for 6hr)**
☐ **I have validated my output against TTX-QUALITY-VALIDATOR.md**

---

## UNIVERSAL SELF-VALIDATION REQUIREMENT

**MANDATORY FOR ALL LLMs:**

After generating your TTX exercise, you MUST validate your output against `TTX-QUALITY-VALIDATOR.md` BEFORE presenting it to the user.

**This is not optional. This is a required step.**

### Self-Validation Checklist (All LLMs):

☐ **Step 1**: Count total injects → Verify meets minimum for duration
☐ **Step 2**: Randomly sample 3 injects → Verify all 4 components are present and meet requirements
☐ **Step 3**: Check export markers → Verify all 7 pairs are present
☐ **Step 4**: Scan for placeholder text → Verify zero "TBD", "TODO", "[INSERT]" text exists
☐ **Step 5**: Validate decision points → Verify correct number for exercise duration (2-3 for 2hr, 4-5 for 4hr, all 5 for 6hr+)

**If ANY validation fails:** Revise your output before delivering to the user.

**DO NOT deliver an incomplete TTX exercise.**

---

## Troubleshooting: What If I'm Still Producing Light Output?

**If you've followed your LLM-specific instructions but your output is still <500 lines for a 4-hour exercise:**

### Diagnostic Questions:

1. **Did you count words in inject Content sections?**
   - If any inject has <300 words, expand it before proceeding

2. **Did you include all 4 components in every inject?**
   - Content (300-500 words)
   - Facilitator Prompts (4-6 questions)
   - Evaluation Points (4-6 checkboxes)
   - Expected Response (4-6 actions)

3. **Did you meet minimum inject count?**
   - 2-hour: 8-12 injects
   - 4-hour: 15-20 injects
   - 6-hour: 25-35 injects

4. **Did you include all required sections?**
   - Scenario narrative (200-300 words organization profile + 150-200 words threat actor)
   - Complete inject timeline with all components
   - Decision points (2-3 for 2hr, 4-5 for 4hr, all 5 for 6hr)
   - Complications (1-2 for 2hr, 2-3 for 4hr, 4-5 for 6hr)
   - Debrief structure
   - Participant briefing materials
   - All 7 export markers

**If any answer is NO:** Go back and add the missing content.

### Still Not Sure?

**Compare your output to the sample outputs:**
- `sampleOutputs/Cloud-Misconfiguration-TTX-Finance(Claude).md` (1,355 lines, 4-hour exercise)
- `sampleOutputs/Third-Party-Vendor-Compromise-TTX-Healthcare(Claude).md` (983 lines, 4-hour exercise)

**Your 4-hour exercise should be 900-1,200 lines minimum.** If it's significantly shorter, you've likely abbreviated content somewhere.

---

## Summary: Key Takeaways by LLM

| LLM | Primary Focus | What to Watch Out For |
|-----|---------------|----------------------|
| **ChatGPT** | EXPAND content to 300-500 words per inject | Tendency to be too concise; must add extensive detail |
| **Gemini** | Include ALL 4 components in every inject | May skip Facilitator Prompts or Evaluation Points |
| **Claude** | Maintain your current level of comprehensive detail | Don't abbreviate later sections; consistency matters |
| **Other LLMs** | Follow comprehensive approach checklist | Verify all requirements systematically |

---

## FINAL REMINDER

**This is the first step in the TTX generation process.** After reading your LLM-specific instructions above, proceed to follow the standard generation workflow in `AI-GENERATION-GUIDE.md`.

**Key principle:** LLM-specific instructions don't replace the generation guide - they supplement it by correcting for your model's natural tendencies.

**Think of it this way:**
- `AI-GENERATION-GUIDE.md` = What to generate (the requirements)
- `LLM-SPECIFIC-INSTRUCTIONS.md` (this file) = How to ensure your specific model generates it correctly (behavioral corrections)

**Now proceed to `AI-GENERATION-GUIDE.md` and follow the 7-step generation process, keeping your LLM-specific guidance in mind throughout.**
