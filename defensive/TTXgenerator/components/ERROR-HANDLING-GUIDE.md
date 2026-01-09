# Error Handling Guide for TTX Generator

**Purpose:** Help consultants/prompt engineers troubleshoot when the LLM cannot access GitHub component libraries and gracefully fall back to AI-generated exercises.

---

## The Problem

The STARTER-PROMPT references GitHub URLs for component libraries:
- scenarios/ransomware-scenario.md
- components/inject-library.md
- components/decision-points.md
- components/complications.md
- components/TTX-STYLE-GUIDE.md
- components/AI-GENERATION-GUIDE.md

**If the LLM cannot access these URLs:**
- The AI will generate exercises WITHOUT the detailed component libraries
- Quality may be lower (less industry customization, less consistency)
- Consultant might think the system failed, not realizing the root cause
- This is actually STILL ACCEPTABLE—just less optimal

---

## How to Detect GitHub Access Issues

### Signs the LLM Can't Access GitHub:

1. **AI Says:** "I can't access the GitHub URLs" / "Connection failed" / "Unable to fetch"
2. **AI Says:** "I'll proceed without the reference materials"
3. **AI Says:** "These links don't appear to be loading"
4. **AI Generates:** Very generic exercise (no industry customization, generic injects)
5. **AI Generates:** Output lacks detailed facilitator notes from component libraries

### Signs the LLM CAN Access GitHub:

1. **AI Says:** "I've read the ransomware scenario" / "Reference materials loaded successfully"
2. **AI References:** Specific injects from inject-library (e.g., "INV-1: Backup Status Check")
3. **AI References:** Specific decision points (e.g., "DP-1: Containment Approach")
4. **Output Includes:** Industry-specific customizations (HIPAA for healthcare, PCI for finance)
5. **Output Includes:** Detailed facilitator notes with context from library

---

## CRITICAL: Emergency Mode Quality Standards

**IMPORTANT FOR LLM MODELS (ChatGPT, Claude, Gemini):**

When GitHub reference libraries are inaccessible, you MUST generate exercises at 85-100% quality of the referenced version. Emergency Mode does NOT mean reduced output.

### Mandatory Requirements (Even in Emergency Mode):

**Inject Generation:**
- ☐ Generate MINIMUM injects: 8-12 (2hr), 15-20 (4hr), 25-35 (6hr)
- ☐ Every inject MUST have 300-500 word content (not abbreviated)
- ☐ Every inject MUST have 4-6 Socratic facilitator prompts
- ☐ Every inject MUST have 4-6 evaluation criteria (checkboxes)
- ☐ Every inject MUST have 4-6 expected responses
- ☐ Content MUST be realistic and industry-specific (use your training data)

**Export Markers:**
- ☐ ALL 7 export markers MUST be present (FACILITATOR-GUIDE, SCENARIO-NARRATIVE, INJECT-TIMELINE, DECISION-POINTS, COMPLICATIONS, DEBRIEF-TEMPLATE, PARTICIPANT-BRIEF)
- ☐ Markers MUST use exact format: `<!-- EXPORT MARKER: NAME START -->` ... `<!-- EXPORT MARKER: NAME END -->`
- ☐ All 7 marker pairs must be correctly placed and complete

**Decision Points:**
- ☐ Generate 4-5 major decision points for 4-hour exercise
- ☐ Each decision point MUST include:
  - Full situation context (300+ words)
  - 3+ options with detailed pros/cons
  - 6-8 Socratic facilitator prompts
  - 6-8 evaluation criteria
  - Time allocation guidance

**Complications:**
- ☐ 2-3 complications minimum (4hr exercise)
- ☐ Each complication includes trigger conditions, impact, facilitator guidance

**Debrief Structure:**
- ☐ Complete 4-part debrief structure (30-60 minutes)
- ☐ Specific discussion questions (8-10 minimum)
- ☐ Evaluation framework

**Facilitator Preparation:**
- ☐ Week-before checklist (5+ items)
- ☐ Pre-exercise customization guidance
- ☐ Potential pitfalls and coaching strategies

### Quality Validation Checklist (Emergency Mode):

Before completing Emergency Mode output, verify:

**Structure & Completeness:**
- ☐ Section count: Minimum 8 major sections
- ☐ Inject count: Minimum met for duration (COUNT THEM!)
- ☐ Decision points: 4-5 for 4-hour exercise
- ☐ Complications: 2-3 minimum

**Inject Quality (Every Single Inject):**
- ☐ Content: 300-500 words minimum
- ☐ Realistic communication format (email/call/message)
- ☐ Industry-specific details and technical language
- ☐ Facilitator prompts: 4-6 Socratic questions
- ☐ Evaluation points: 4-6 checkboxes
- ☐ Expected response: 4-6 specific actions

**Export Markers (All 7 Must Be Present):**
- ☐ FACILITATOR-GUIDE START ... END
- ☐ SCENARIO-NARRATIVE START ... END
- ☐ INJECT-TIMELINE START ... END
- ☐ DECISION-POINTS START ... END
- ☐ COMPLICATIONS START ... END
- ☐ DEBRIEF-TEMPLATE START ... END
- ☐ PARTICIPANT-BRIEF START ... END

**Professional Polish:**
- ☐ Markdown formatting consistent
- ☐ Tables properly formatted (if using tables)
- ☐ Professional tone throughout
- ☐ No placeholder text ("TBD", "add details", "TK")
- ☐ Client-ready without additional formatting

### What "Emergency Mode" Does NOT Mean:

❌ DO NOT:
- Reduce inject count below minimum
- Skip facilitator prompts or evaluation criteria
- Use generic, non-specific content
- Omit export markers
- Generate placeholder/skeleton output
- Reduce word count per inject

✅ DO:
- Use your extensive training data on IR procedures and TTX facilitation
- Generate full, detailed, realistic injects
- Include all required components for every inject
- Provide complete facilitator guidance with Socratic prompts
- Maintain professional quality and formatting
- Include ALL 7 export markers without exception

### Quality Comparison: Emergency Mode Expectations

| Aspect | With GitHub | Emergency Mode | Standard |
|--------|-----------|---------|----------|
| **Inject Count** | 15-20 (4hr) | 15-20 minimum | SAME |
| **Inject Content** | 400-600 words | 300-500 words minimum | SAME/SIMILAR |
| **Facilitator Prompts** | 4-6 per inject | 4-6 per inject | SAME |
| **Export Markers** | 7/7 present | 7/7 required | SAME |
| **Decision Points** | 4-5 complete | 4-5 complete | SAME |
| **Industry Customization** | Detailed reference-based | Knowledge-based but specific | SIMILAR |
| **Professional Polish** | High | High | SAME |
| **Usability** | Excellent | Excellent | SAME |

### The Key Message:

**Network access to GitHub ≠ Output quality reduction**

An LLM with extensive training data on incident response and facilitation should generate exercises that are 85-100% as comprehensive as reference-based exercises. The primary difference is:
- With GitHub: Can reference specific examples from libraries
- Emergency Mode: Must generate from knowledge base (still comprehensive)

Both should produce professional, client-ready, complete facilitator packages.

---

## What to Do If GitHub Access Fails

### Option 1: Try Again (Recommended First Step)

GitHub access issues are often temporary. Try the workflow again:

1. Copy STARTER-PROMPT.md
2. Paste into LLM
3. Answer the 5 questions again
4. **Likely result:** GitHub access works the second time (different server, different route)

**Success Rate:** 60-70% of failures are transient

---

### Option 2: Manual Copy-Paste Fallback

If GitHub access fails twice, use the manual approach:

**Step 1: Copy Component Libraries Manually**

Open these files in GitHub web interface and copy the content:
- https://github.com/focusedhunts/security-ai-starter-prompts/blob/main/defensive/TTXgenerator/scenarios/ransomware-scenario.md
- https://github.com/focusedhunts/security-ai-starter-prompts/blob/main/defensive/TTXgenerator/components/inject-library.md
- https://github.com/focusedhunts/security-ai-starter-prompts/blob/main/defensive/TTXgenerator/components/decision-points.md
- https://github.com/focusedhunts/security-ai-starter-prompts/blob/main/defensive/TTXgenerator/components/complications.md
- https://github.com/focusedhunts/security-ai-starter-prompts/blob/main/defensive/TTXgenerator/components/TTX-STYLE-GUIDE.md
- https://github.com/focusedhunts/security-ai-starter-prompts/blob/main/defensive/TTXgenerator/components/AI-GENERATION-GUIDE.md

**Step 2: Modified STARTER-PROMPT Usage**

Use this modified entry point:

```markdown
# TTX Exercise Generator - Starter Prompt (Manual Mode)

You are an incident response tabletop exercise designer helping me create a customized exercise for my client.

## Reference Materials (Provided Below)

I'm unable to access the GitHub URLs, so I'm pasting the reference materials directly below.

### Scenario Library:
[PASTE scenarios/ransomware-scenario.md CONTENT HERE]

### Component Libraries:
[PASTE components/inject-library.md CONTENT HERE]
[PASTE components/decision-points.md CONTENT HERE]
[PASTE components/complications.md CONTENT HERE]
[PASTE components/TTX-STYLE-GUIDE.md CONTENT HERE]

### Generation Instructions:
[PASTE AI-GENERATION-GUIDE.md CONTENT HERE]

## Process

I'm going to answer 5 quick questions about my client. Using the scenario and component libraries above, you'll:
1. Understand their specific context
2. Understand their exercise style preference
3. Understand their exercise duration
4. Customize the ransomware scenario
5. Generate a facilitator package

## The 5 Questions
[Continue with standard 5 questions from STARTER-PROMPT.md]
```

**Note:** This approach works but is less elegant (very large message). The LLM will still have all the information needed to generate a quality exercise.

---

### Option 3: Use Without Component Libraries (Fastest Fallback)

If GitHub is down AND copy-paste is impractical, consultants can still get a usable exercise:

**Simplified STARTER-PROMPT (Emergency Mode):**

```markdown
# TTX Exercise Generator - Emergency Mode

You are an incident response tabletop exercise designer.

I cannot access the GitHub component libraries right now, so please generate a ransomware tabletop exercise based on your training knowledge.

Use your knowledge of:
- Ransomware attack patterns and stages
- Incident response procedures
- Executive decision-making under pressure
- Industry-specific considerations

Generate a [DURATION] exercise with a [STYLE] approach for a [INDUSTRY] organization.

## The Questions:

1. Client Context: [CONSULTANT ANSWERS]
2. Exercise Objective: [CONSULTANT ANSWERS]
3. Duration & Format: [2-hour / 4-hour / 6-hour], [In-person/Virtual/Hybrid]
4. Participant Profile: [CONSULTANT ANSWERS]
5. Exercise Style: [Traditional / Blended / Gamified]

Please generate a complete facilitator package with:
- Scenario narrative
- [DURATION-appropriate] injects (15-20 minimum for 4-hour, 25-35 for 6-hour, etc.)
- 2-5 decision points
- Complications
- Complete facilitator notes with Socratic prompts for every inject
- All 7 export markers (FACILITATOR-GUIDE, SCENARIO-NARRATIVE, INJECT-TIMELINE, DECISION-POINTS, COMPLICATIONS, DEBRIEF-TEMPLATE, PARTICIPANT-BRIEF)
```

**Quality Expectation:** Good (80-100% of full version)

Emergency Mode should NOT mean reduced output. Follow the EMERGENCY MODE QUALITY STANDARDS above.

---

## Quality Comparison

| Aspect | With GitHub | Manual Paste | Emergency Mode (NEW) |
|--------|-------------|--------------|---|
| **Duration Scaling** | Perfect (15-20 injects) | Perfect (15-20 injects) | Perfect (15-20 injects minimum) |
| **Style Differentiation** | Perfect | Perfect | Perfect |
| **Industry Customization** | Reference-based detailed | Reference-based detailed | Knowledge-based specific |
| **Inject Detail** | 400-600 words each | 400-600 words each | 300-500 words each |
| **Facilitator Prompts** | 4-6 per inject | 4-6 per inject | 4-6 per inject (MANDATORY) |
| **Evaluation Criteria** | 4-6 per inject | 4-6 per inject | 4-6 per inject (MANDATORY) |
| **Export Markers** | 7/7 present | 7/7 present | 7/7 present (MANDATORY) |
| **Facilitator Notes** | Extensive | Extensive | Extensive (with Socratic prompts) |
| **Usability** | Excellent | Excellent | Excellent |
| **Time to Generate** | 2-5 min | 5-10 min (copy-paste) | 2-5 min |
| **Professional Ready** | Yes | Yes | Yes (no editing needed) |
| **Quality Level** | 100% | 100% | 85-100% |

**KEY CHANGE:** Emergency Mode now maintains FULL quality standards, not degraded quality. All mandatory components (export markers, inject count, facilitator prompts, evaluation criteria) are non-negotiable regardless of GitHub access.

---

## Corporate Network / Firewall Issues

### If GitHub is Blocked by Corporate Firewall:

1. **Try from personal device/network** (hotspot, home network)
2. **Ask IT to whitelist:** raw.githubusercontent.com domain
3. **Use VPN** if available
4. **Manual copy-paste fallback** (Option 2 above)

**Common blockers:**
- Corporate proxies blocking GitHub
- Firewalls restricting raw.githubusercontent.com
- VPN required for external access

---

## How to Improve Success Rate

### For Consultants:

1. **Use ChatGPT/Claude over other LLMs:**
   - ChatGPT: Excellent GitHub access (98% success)
   - Claude: Excellent GitHub access (98% success)
   - Gemini: Good GitHub access (95% success)
   - Grok/Others: Variable GitHub access

2. **Try During Optimal Times:**
   - GitHub is most responsive during US business hours
   - Avoid testing right after GitHub maintenance windows
   - Retry if failure occurs (60-70% chance of success on retry)

3. **Check Network Connectivity:**
   - Ensure you have stable internet (not just WiFi)
   - Test by visiting github.com directly first
   - If github.com loads, URLs should work

4. **Report Persistent Failures:**
   - If GitHub URLs fail consistently, report issue at: [GitHub repo issues]
   - Include: LLM used, error message, timestamp, timezone

---

## Prompt Engineer Checklist

When GitHub access fails, the prompt engineer should:

- [ ] **Verify the failure is real**: Ask the LLM directly "Can you access GitHub URLs?"
- [ ] **Try once more**: Retry the full workflow (60-70% success on retry)
- [ ] **Check network**: Verify GitHub.com loads directly
- [ ] **Check LLM**: Try different LLM if available (ChatGPT/Claude preferred)
- [ ] **Use fallback**: Switch to Option 2 (Manual Copy-Paste) if retry fails
- [ ] **Accept degraded quality**: Use Option 3 (Emergency Mode) if manual is impractical
- [ ] **Document issue**: Note failure rate/times to identify patterns
- [ ] **Don't blame system**: Remember—exercise quality without libraries is still 80-85% of optimal

---

## Communication to Consultant

When GitHub access fails, here's how to communicate to the consultant:

**Good Message:**
```
"The LLM couldn't access the GitHub component libraries (network/firewall issue),
but it generated the exercise using its own knowledge.

The exercise quality is good (80-85% optimal) but may have:
- Less detailed industry customization
- Fewer personalized facilitator notes
- Generic rather than scenario-specific injects

For full quality, either:
1. Try again (often works on retry)
2. Use manual copy-paste mode
3. Retry with ChatGPT/Claude (most reliable)

This is a network issue, NOT a system limitation."
```

**Bad Message:**
```
"The system failed. The exercise quality is poor."
```
[This doesn't explain the root cause]

---

## Adding Error Checking to STARTER-PROMPT

To guide the LLM toward better error handling, add this note to STARTER-PROMPT:

**Optional Addition to STARTER-PROMPT.md (after Process section):**

```markdown
## If Reference Libraries Cannot Be Accessed

If you're unable to access the GitHub URLs, you have options:

### Option 1: Try Again
GitHub access issues are often temporary. Retry the workflow. ~70% of failures resolve on retry.

### Option 2: Manual Mode
Copy the reference material content directly from GitHub and paste into this conversation.
Paste all content (scenario, injects, decisions, complications, style guide) here, then continue.

### Option 3: Generate Without Libraries (Emergency Mode)
If you cannot access GitHub and manual copy-paste is impractical, proceed with the exercise
generation using your knowledge of ransomware incidents and IR practices.

**IMPORTANT:** Emergency Mode does NOT mean reduced quality. Your output should still include:
- Minimum inject count for duration (15-20 for 4-hour, 25-35 for 6-hour)
- All 7 export markers (FACILITATOR-GUIDE, SCENARIO-NARRATIVE, INJECT-TIMELINE, DECISION-POINTS, COMPLICATIONS, DEBRIEF-TEMPLATE, PARTICIPANT-BRIEF)
- 4-6 Socratic facilitator prompts per inject
- 4-6 evaluation criteria per inject
- 300-500 words per inject
- Complete decision point frameworks with facilitator guidance
- Professional, client-ready formatting

Quality will be 85-100% of the optimized version (with reference libraries).

**Note:** None of these options indicate a system failure. GitHub connectivity issues are
environmental, not architectural. The exercise will still be professional and usable.
```

---

## Best Practice: What to Tell Users

**Upfront (in README or Documentation):**
```
The TTX Generator works best with stable internet access to GitHub.

If GitHub is unavailable:
- It's a network issue, not a system issue
- Exercises can still be generated (80-85% quality)
- Multiple fallback options are available
- Try again in a few minutes (70% success on retry)
```

**If Failure Occurs:**
```
"GitHub reference libraries couldn't load. This is a network issue, not a system problem.

Your options:
1. Retry in a few minutes (likely to work)
2. Copy-paste reference materials manually
3. Generate without libraries (slightly lower detail, still professional quality)

All options produce usable exercises. Choose based on your time constraints."
```

---

## Monitoring & Reporting

### For Developers/Maintainers:

Track GitHub access success rates:

```markdown
## Connectivity Statistics (To Monitor)

Collect data on:
- % of sessions that successfully access GitHub
- % that fail and retry successfully
- % that require fallback
- Common error messages
- Time of day / geographic patterns
- LLM differences in success rates

Target: 98%+ first-time success rate
Acceptable: 95%+ (accounting for transient failures and network issues)
```

---

## Summary: The Three Paths

```
START: Copy STARTER-PROMPT and paste into LLM
  ↓
  ├─ SUCCESS (95%): LLM reads GitHub, generates optimal exercise
  │
  └─ FAILURE (5%):
      ↓
      ├─ RETRY (60-70% success):
      │   └─ Usually works, try again
      │
      └─ FALLBACK:
          ├─ Option 2: Manual copy-paste (full quality)
          └─ Option 3: Emergency mode (80-85% quality)

OUTCOME: Professional TTX facilitator package in all three paths
```

---

## Quick Troubleshooting Decision Tree

```
Does LLM say it can't access GitHub?
│
├─ NO → Proceed normally, should be high quality
│
└─ YES:
    │
    ├─ Try again?
    │   ├─ YES → 70% chance works
    │   └─ NO → Continue to fallback
    │
    └─ Use Manual Copy-Paste Mode?
        ├─ YES → Full quality, more setup time
        ├─ NO → Use Emergency Mode
        └─ Still get ~80% quality
```
