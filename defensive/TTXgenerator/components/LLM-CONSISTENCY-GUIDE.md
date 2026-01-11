# LLM Consistency Guide for TTX Generator Users

**Purpose:** This guide explains how the TTX Generator ensures consistent output quality across different Large Language Models (LLMs) and what you should expect when using different AI platforms.

**Last Updated:** January 2026

---

## Why This Guide Exists

The TTX Generator is designed to work with any modern LLM (ChatGPT, Claude, Gemini, etc.). However, different LLMs have different natural behaviors:

- **Some LLMs are naturally concise** and may produce shorter outputs
- **Some LLMs are naturally verbose** and produce longer, more detailed outputs
- **Some LLMs focus on structure** while others emphasize narrative content
- **Some LLMs may skip components** they perceive as "optional"

These differences can lead to inconsistent output quality, where one LLM produces a 200-line facilitator package while another produces a 1,200-line package for the same exercise parameters.

**This is now fixed.** The TTX Generator includes LLM-specific instructions that correct for these behavioral differences, ensuring consistent, high-quality output regardless of which LLM you use.

---

## What Changed (January 2026 Update)

### Before This Update:
- **ChatGPT**: Produced concise outputs (~200-300 lines for 4-hour exercises) with abbreviated facilitator guidance
- **Gemini**: Produced structured but light outputs (~200-300 lines) sometimes missing facilitator prompts
- **Claude**: Produced comprehensive outputs (~900-1,200 lines) with extensive facilitator guidance

**Result:** Inconsistent quality across LLMs; users couldn't switch between LLMs without quality degradation.

### After This Update:
- **ChatGPT**: Now produces comprehensive outputs (900-1,200 lines for 4-hour exercises) with expanded content and extensive facilitator guidance
- **Gemini**: Now produces comprehensive outputs (900-1,200 lines) with complete component coverage
- **Claude**: Maintains comprehensive outputs (900-1,200 lines) at current quality level

**Result:** Consistent quality across all LLMs; users can choose any LLM and receive immediately usable facilitator packages.

---

## How It Works

### The LLM Self-Identification System

When you paste the `STARTER-PROMPT.md` into an LLM, the system now:

1. **Asks the LLM to self-identify** - "Are you ChatGPT, Claude, Gemini, or another model?"
2. **Routes to LLM-specific instructions** - The LLM reads tailored guidance addressing its natural behavioral tendencies
3. **Applies behavioral corrections** - The LLM adjusts its generation approach to meet consistent quality standards
4. **Self-validates before delivery** - The LLM checks its own output against the quality validator before presenting to you

**This all happens automatically**. You don't need to do anything differently.

### What Each LLM Is Told

**ChatGPT is told:**
- "Your natural style is concise. For TTX generation, verbose is better."
- "You MUST expand every inject to 300-500 words minimum. Count the words."
- "Include extensive facilitator notes, not just participant content."

**Gemini is told:**
- "Facilitator Prompts and Evaluation Points are NOT optional. Every inject must have them."
- "Don't assume the user can 'fill in the blanks' - provide complete, explicit detail."
- "Expected Response sections need 4-6 specific action items, not brief summaries."

**Claude is told:**
- "Your natural thoroughness is ideal for this task. Continue producing detailed outputs."
- "Maintain your current level of detail throughout all sections."
- "Don't try to be more concise - consistency and comprehensiveness matter."

---

## What to Expect from Each LLM

### ChatGPT (GPT-4, GPT-4o, GPT-3.5)

**Expected Output for 4-Hour Exercise:**
- **Line Count:** 900-1,200 lines (significantly increased from previous ~200-300 lines)
- **Inject Count:** 15-20 injects, each with 300-500 word content
- **Facilitator Guidance:** Extensive Socratic questions (4-6 per inject)
- **Evaluation Criteria:** Comprehensive checkboxes (4-6 per inject)
- **Style:** Clear, well-structured, highly organized

**Strengths:**
- Excellent structure and readability
- Clear section organization
- Good adherence to templates
- Professional formatting

**What Changed:**
- Content is now significantly more detailed
- Facilitator prompts are now extensive and Socratic
- No more abbreviated or "efficient" responses

**When to Use ChatGPT:**
- You want clear, well-organized facilitator packages
- You prefer highly structured outputs
- You need consistent formatting
- You're working with teams new to TTX exercises (clarity helps)

### Gemini (Gemini Pro, Gemini Ultra, Gemini Advanced)

**Expected Output for 4-Hour Exercise:**
- **Line Count:** 900-1,200 lines (significantly increased from previous ~200-300 lines)
- **Inject Count:** 15-20 injects, each with complete components
- **Facilitator Guidance:** Complete Socratic questions (4-6 per inject)
- **Evaluation Criteria:** Comprehensive checkboxes (4-6 per inject)
- **Style:** Structured, analytical, thorough

**Strengths:**
- Excellent analytical organization
- Strong logical flow
- Good at complex multi-step instructions
- Thorough when explicitly prompted

**What Changed:**
- Facilitator Prompts and Evaluation Points are now always included
- Expected Response sections are now fully detailed
- No more structural frameworks without content depth

**When to Use Gemini:**
- You want analytical, logically structured facilitator packages
- You prefer systematic organization
- You need strong adherence to multi-step processes
- You're working with technically sophisticated audiences

### Claude (Sonnet, Opus, Haiku, 3.5)

**Expected Output for 4-Hour Exercise:**
- **Line Count:** 900-1,200 lines (maintained from previous outputs)
- **Inject Count:** 15-20 injects, each with comprehensive content
- **Facilitator Guidance:** Extensive Socratic questions with nuanced exploration
- **Evaluation Criteria:** Detailed checkboxes with process focus
- **Style:** Comprehensive, nuanced, balanced technical + business context

**Strengths:**
- Naturally comprehensive outputs
- Excellent at Socratic facilitation guidance
- Strong balance of technical detail and business context
- Explores nuances and edge cases
- Rich scenario narratives

**What Changed:**
- Minimal changes needed (Claude was already the quality baseline)
- Now includes explicit reminders to maintain consistency throughout

**When to Use Claude:**
- You want the most comprehensive facilitator packages
- You prefer nuanced, exploration-focused facilitation guidance
- You need balanced technical + business context
- You're working with mature IR teams that benefit from depth

### Other LLMs (Llama, Mistral, Cohere, etc.)

**Expected Output for 4-Hour Exercise:**
- **Line Count:** 900-1,200 lines (following comprehensive approach guidelines)
- **Inject Count:** 15-20 injects with all required components
- **Facilitator Guidance:** 4-6 Socratic questions per inject
- **Evaluation Criteria:** 4-6 checkboxes per inject
- **Style:** Varies by model but follows standardized requirements

**When to Use:**
- You have access to other LLMs and want to experiment
- You're testing newer models for TTX generation
- You need to work within specific deployment constraints (on-prem models, etc.)

---

## How to Verify Output Quality

After generating a TTX exercise with any LLM, you can quickly verify it meets quality standards.

### Quick Validation Checks

#### 1. Line Count Check
```bash
# On Linux/Mac:
wc -l your-output.md

# On Windows PowerShell:
(Get-Content your-output.md).Count
```

**Expected for 4-hour exercise:** 900-1,200 lines minimum

**If significantly less:** The LLM may have abbreviated content. Ask it to "regenerate with full detail per LLM-SPECIFIC-INSTRUCTIONS.md"

#### 2. Inject Count Check
```bash
# Count inject occurrences:
grep -c "^## INJECT" your-output.md  # Linux/Mac
Select-String -Pattern "^## INJECT" -Path your-output.md | Measure-Object | Select-Object -ExpandProperty Count  # Windows PowerShell
```

**Expected for 4-hour exercise:** 15-20 injects minimum

**If fewer than 15:** The exercise is incomplete. Ask the LLM to add more injects.

#### 3. Export Marker Check
```bash
# Count export markers:
grep -c "EXPORT MARKER" your-output.md  # Linux/Mac
(Select-String -Pattern "EXPORT MARKER" -Path your-output.md).Count  # Windows PowerShell
```

**Expected:** 14 markers (7 START + 7 END pairs)

**If fewer than 14:** Export markers are missing. This will make section extraction difficult.

#### 4. Placeholder Text Check
```bash
# Check for incomplete content:
grep -i "TBD\|TODO\|PLACEHOLDER\|INSERT" your-output.md  # Linux/Mac
Select-String -Pattern "TBD|TODO|PLACEHOLDER|INSERT" -Path your-output.md  # Windows PowerShell
```

**Expected:** No results (zero placeholder text)

**If found:** The LLM didn't complete generation. Ask it to replace all placeholder text with actual content.

### Manual Spot Check

**Randomly select 3 injects and verify each has:**

☐ **Content section**: 300-500 words with specific details (system names, timestamps, technical context)

☐ **Facilitator Prompts**: 4-6 Socratic questions (e.g., "What's your confidence level that...?", "Before we decide..., what information do you need?")

☐ **Evaluation Points**: 4-6 checkboxes with observable behaviors (☐ Team escalates immediately, ☐ Team requests additional context, etc.)

☐ **Expected Response**: 4-6 detailed action items (not just "investigate" - specific actions with WHO/WHAT/WHEN)

**If any component is missing or abbreviated:** The LLM may have skipped components. Ask it to expand the specific injects with missing content.

---

## Troubleshooting: What If Output Is Still Light?

### Problem: ChatGPT Still Produces <500 Lines for 4-Hour Exercise

**Likely Cause:** ChatGPT may have skipped the LLM-specific instructions or abbreviated despite them.

**Solution:**
1. Check that STARTER-PROMPT.md includes the LLM self-identification section
2. Explicitly prompt: "I need you to follow the ChatGPT-specific instructions in LLM-SPECIFIC-INSTRUCTIONS.md. Expand every inject to 300-500 words and include extensive facilitator guidance."
3. Ask: "Please regenerate this exercise with full detail - every inject should have 300-500 word content sections, 4-6 facilitator prompts, 4-6 evaluation points, and 4-6 expected response items."

### Problem: Gemini Produces Injects Without Facilitator Prompts

**Likely Cause:** Gemini may have treated Facilitator Prompts as optional.

**Solution:**
1. Explicitly prompt: "Every inject MUST include a Facilitator Prompts section with 4-6 Socratic questions. This is not optional."
2. Ask: "Please review all injects and add Facilitator Prompts to any that are missing this section."
3. Provide an example of a complete inject and ask Gemini to match that format.

### Problem: Output Has Placeholder Text ("TBD", "INSERT DETAILS HERE")

**Likely Cause:** The LLM ran out of time or didn't fully complete generation.

**Solution:**
1. Identify specific sections with placeholder text
2. Prompt: "Please replace all TBD/placeholder text with actual detailed content. Search for 'TBD', 'TODO', 'INSERT', and '[PLACEHOLDER]' in your output and complete those sections."
3. If extensive placeholders exist, ask the LLM to regenerate the entire exercise.

### Problem: Claude Output Is Too Long (>1,500 Lines)

**Likely Cause:** This is actually not a problem - Claude is naturally comprehensive.

**Solution:**
- **Don't reduce content** - comprehensive is better than abbreviated for TTX
- Use export markers to extract sections for different audiences (facilitators get full guide, participants get briefing only)
- If truly excessive, check for redundancy (same content repeated multiple times) and ask Claude to consolidate

### Problem: Inject Count Is Below Minimum (e.g., Only 10 Injects for 4-Hour Exercise)

**Likely Cause:** The LLM didn't meet the mandatory minimum inject count requirements.

**Solution:**
1. Check the inject count requirements in AI-GENERATION-GUIDE.md:
   - 2-hour: 8-12 injects minimum
   - 4-hour: 15-20 injects minimum
   - 6-hour: 25-35 injects minimum
2. Prompt: "This exercise has only [X] injects but requires a minimum of [Y] for a [duration]-hour exercise. Please add [Y-X] more injects distributed across the investigation, response, and recovery phases."
3. Reference the inject-library.md for additional inject ideas

---

## Comparison Table: Before vs. After

| Aspect | ChatGPT Before | ChatGPT After | Gemini Before | Gemini After | Claude Before | Claude After |
|--------|---------------|--------------|--------------|-------------|--------------|-------------|
| **Line Count (4hr)** | ~200-300 | ~900-1,200 | ~200-300 | ~900-1,200 | ~900-1,200 | ~900-1,200 |
| **Inject Count (4hr)** | 12-15 | 15-20 | 12-15 | 15-20 | 15-20 | 15-20 |
| **Content per Inject** | 100-200 words | 300-500 words | 150-250 words | 300-500 words | 300-500 words | 300-500 words |
| **Facilitator Prompts** | 1-3 per inject | 4-6 per inject | Sometimes missing | 4-6 per inject | 4-6 per inject | 4-6 per inject |
| **Evaluation Points** | 2-3 per inject | 4-6 per inject | Sometimes missing | 4-6 per inject | 4-6 per inject | 4-6 per inject |
| **Immediately Usable?** | No (needs expansion) | Yes | No (needs completion) | Yes | Yes | Yes |

---

## Best Practices for Users

### 1. Start with the Correct Prompt

Always use the updated `STARTER-PROMPT.md` that includes LLM self-identification instructions. The older version without LLM-specific routing will not produce consistent results.

**Check that your STARTER-PROMPT.md includes:**
- Section titled "IMPORTANT: LLM Self-Identification Required"
- Reference to `LLM-SPECIFIC-INSTRUCTIONS.md`
- Validation reminder at the end

### 2. Choose Your LLM Based on Strengths

**For maximum comprehensiveness:** Use Claude
**For clearest structure:** Use ChatGPT
**For analytical organization:** Use Gemini

**All three now produce equivalent quality** - choose based on stylistic preference, not quality concerns.

### 3. Validate Every Output

Even with LLM-specific instructions, always run quick validation checks:
- ☐ Line count meets expected range for duration
- ☐ Inject count meets minimum for duration
- ☐ Export markers all present (14 total)
- ☐ No placeholder text exists
- ☐ Spot check 3 random injects for completeness

### 4. Provide Feedback

If an LLM consistently produces subpar output despite LLM-specific instructions:
- Document the specific issue (missing components, abbreviated content, etc.)
- Try explicitly referencing the LLM-SPECIFIC-INSTRUCTIONS.md in your prompt
- Report the issue so we can further refine the LLM-specific guidance

### 5. Use Export Markers

All LLMs now include export markers for section extraction. Use these to:
- Extract FACILITATOR-GUIDE for your own use
- Extract SCENARIO-NARRATIVE for participant preview
- Extract PARTICIPANT-BRIEF for pre-exercise distribution
- Extract DEBRIEF-TEMPLATE for post-exercise review

**This prevents you from having to manually separate sections.**

---

## FAQ

### Q: Which LLM should I use?

**A:** All three major LLMs (ChatGPT, Claude, Gemini) now produce equivalent quality. Choose based on:
- **Access**: Which LLM do you have a subscription to?
- **Style preference**: Do you prefer ChatGPT's clarity, Claude's depth, or Gemini's structure?
- **Organizational requirements**: Some organizations mandate specific LLMs

**Quality is no longer a differentiator** - all three are now consistent.

### Q: What if I'm using an older version of the starter prompt?

**A:** Update to the latest `STARTER-PROMPT.md` that includes LLM self-identification. The older version will produce inconsistent results because it lacks LLM-specific behavioral corrections.

**To check if you have the updated version:**
- Look for a section titled "IMPORTANT: LLM Self-Identification Required" near the beginning
- Look for reference to `LLM-SPECIFIC-INSTRUCTIONS.md`
- Check that TTX-QUALITY-VALIDATOR.md includes a "MANDATORY SELF-VALIDATION" section

### Q: Can I still use older sample outputs?

**A:** Yes. Older sample outputs remain valid examples of what comprehensive TTX exercises look like. However, newer outputs generated with LLM-specific instructions will be more consistent across different LLMs.

### Q: What if my organization uses a custom or proprietary LLM?

**A:** The LLM-SPECIFIC-INSTRUCTIONS.md includes a section for "Other LLMs" that provides comprehensive approach guidelines. Custom LLMs should follow those default instructions.

**If your custom LLM consistently produces incomplete output:**
- Consider creating custom LLM-specific instructions based on the patterns you observe
- Add these instructions to the "Other LLMs" section of LLM-SPECIFIC-INSTRUCTIONS.md
- Share your custom instructions with the community if possible

### Q: Do I need to change anything in how I use the TTX Generator?

**A:** No. The LLM-specific instructions operate automatically once you use the updated STARTER-PROMPT.md. You don't need to change your workflow.

**Just ensure you're using the updated version of:**
- STARTER-PROMPT.md (includes LLM self-identification)
- LLM-SPECIFIC-INSTRUCTIONS.md (the new file created for this update)
- AI-GENERATION-GUIDE.md (strengthened mandatory language)
- TTX-QUALITY-VALIDATOR.md (includes mandatory self-validation)

### Q: What if I find a bug or inconsistency?

**A:** Please report issues with specific details:
- Which LLM you used
- What exercise parameters you specified (scenario, duration, style, etc.)
- What output quality issue you observed (missing components, abbreviated content, etc.)
- Whether you used the updated STARTER-PROMPT.md with LLM self-identification

**This helps us refine LLM-specific instructions over time.**

---

## Technical Details (For Advanced Users)

### How LLM Self-Identification Works

**Step 1: Detection**
The LLM reads the prompt and encounters the self-identification instruction: "Identify which LLM you are."

**Step 2: Routing**
The LLM self-identifies based on its training: "I am ChatGPT" / "I am Claude" / "I am Gemini"

**Step 3: Behavioral Correction**
The LLM reads the corresponding section of LLM-SPECIFIC-INSTRUCTIONS.md that addresses its natural tendencies.

**Step 4: Generation**
The LLM follows the standard AI-GENERATION-GUIDE.md workflow while keeping its LLM-specific behavioral corrections in mind.

**Step 5: Self-Validation**
Before delivering output, the LLM validates its work against TTX-QUALITY-VALIDATOR.md and revises if necessary.

### Why This Approach Works

**Alternative approaches we considered:**
1. **Separate starter prompts per LLM** - Rejected: Too much duplication, harder to maintain
2. **External validation script** - Rejected: Breaks the prompt-as-infrastructure philosophy
3. **Reduce Claude's verbosity** - Rejected: User feedback preferred increasing detail in lighter outputs

**Our approach (LLM self-identification + behavioral corrections):**
- ✅ Maintains single source of truth (one STARTER-PROMPT.md)
- ✅ LLM-native (no external code dependencies)
- ✅ Addresses root cause (LLM interpretation variance)
- ✅ Scales to new LLMs easily (just add new section to LLM-SPECIFIC-INSTRUCTIONS.md)
- ✅ Transparent to users (happens automatically)

### File Structure After Update

```
TTXgenerator/
├── STARTER-PROMPT.md (modified - includes LLM self-identification)
├── components/
│   ├── AI-GENERATION-GUIDE.md (modified - strengthened requirements, added pre-generation checklist)
│   ├── TTX-QUALITY-VALIDATOR.md (modified - added mandatory self-validation section)
│   ├── LLM-SPECIFIC-INSTRUCTIONS.md (NEW - LLM-specific behavioral corrections)
│   ├── LLM-CONSISTENCY-GUIDE.md (NEW - this user guide)
│   ├── inject-library.md (unchanged)
│   ├── decision-points.md (unchanged)
│   ├── complications.md (unchanged)
│   └── TTX-STYLE-GUIDE.md (unchanged)
└── scenarios/ (all unchanged)
```

---

## Summary

The TTX Generator now ensures **consistent, high-quality output across all major LLMs** through LLM-specific behavioral corrections and mandatory self-validation.

**Key Changes:**
- ✅ ChatGPT now produces comprehensive outputs (900-1,200 lines for 4hr exercises)
- ✅ Gemini now includes all required components (facilitator prompts, evaluation points, etc.)
- ✅ Claude maintains its comprehensive quality level
- ✅ All LLMs self-validate before delivering output
- ✅ Users can switch between LLMs without quality concerns

**What You Need to Do:**
1. Use the updated STARTER-PROMPT.md (includes LLM self-identification)
2. Validate output with quick checks (line count, inject count, export markers, no placeholders)
3. Choose your preferred LLM based on style preference (all three are now equivalent quality)

**Questions or Issues?**
- Reference this guide for troubleshooting steps
- Check that you're using updated versions of all component files
- Report persistent issues with specific details for further refinement

**The TTX Generator now works consistently with any major LLM. Happy facilitating!**
