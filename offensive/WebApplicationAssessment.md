# Red Team Operations: Starter Prompts for AI-Assisted Offensive Security

## ⚠️ CRITICAL LEGAL AND ETHICAL NOTICE

**ALL PROMPTS IN THIS DOCUMENT ASSUME PROPER AUTHORIZATION**

These starter prompts are designed to help authorized security professionals use AI effectively during legitimate security assessments. Using these techniques without proper authorization is illegal.

**Requirements for use:**
- Written authorization (contract, Statement of Work, bug bounty program rules)
- Clearly defined scope and boundaries
- Legal review of engagement terms
- Professional liability protections

**The authors bear NO responsibility for unauthorized use of these techniques.**

---

## How to Use These Starter Prompts

These are **templates** to help you craft effective AI prompts for specific red team tasks. They are NOT complete operational guides.

**For each starter prompt:**

1. **Read the task description** - Understand what operational need this addresses
2. **Fill in YOUR context** - Replace placeholders with your engagement details
3. **Adjust for your specificity needs** - Add/remove detail based on your situation
4. **Iterate based on AI responses** - Refine your prompts as the AI provides output
5. **Verify all AI outputs** - Never use AI-generated content without validation

**🏢 vs 🌐 Guidance:**
- 🏢 = Safe to include when using enterprise AI with data processing agreements
- 🌐 = Keep generic when using consumer AI services

---

## Penetration Tester Prompts

### Prompt 1: Web Application Attack Surface Analysis

**When to use this:** You've completed initial reconnaissance of a web application and need to systematically identify potential vulnerability areas and testing priorities for your authorized penetration test.

**Why this is a separate prompt:** Attack surface analysis should happen BEFORE exploitation attempts. This prompt helps you think through what to test without prematurely jumping into exploitation. It's a planning/analysis task, not a doing task.

**Four Principles Application:**
- **Context:** You provide engagement scope, discovered technology, and authorization boundaries
- **Specificity:** You specify the exact application features and endpoints you discovered
- **Structure:** The prompt guides you to organize findings by attack category
- **Iteration:** Start with this analysis, then create separate prompts for testing each identified area

---

**⚠️ AUTHORIZATION CHECKPOINT**

Before using this prompt, confirm you have:
- [ ] Written authorization for this specific application/domain
- [ ] Clear scope definition (what's in/out of bounds)
- [ ] Client contact for scope questions
- [ ] Authorized testing timeframe

If ANY box is unchecked, STOP and obtain proper authorization.

---

**STARTER PROMPT TEMPLATE:**

```markdown
I am conducting an authorized penetration test and need help analyzing the attack surface of a web application to identify potential vulnerability areas and prioritize my testing approach.

ENGAGEMENT AUTHORIZATION:
Client: [YOUR_CLIENT_NAME]
🏢 Enterprise: "HealthTech Solutions Inc. - Contract #PT-2024-156"
🌐 Consumer: "Authorized client under contract"

Application: [APPLICATION_NAME and PURPOSE]
🏢 Enterprise: "PatientPortal v3.2 - Healthcare records management system"
🌐 Consumer: "Web application for [business function]"

Testing Scope: [WHAT'S AUTHORIZED]
🏢 Enterprise: "All features at https://staging.patientportal.example.com - Staging environment only. Production explicitly OUT OF SCOPE."
🌐 Consumer: "Testing authorized on [specific URLs/domains only]"

Prohibited Actions: [EXPLICIT RESTRICTIONS]
Example: "No denial of service, no social engineering of employees, no testing of payment processor integration"

Testing Timeline: [DATES/HOURS]
Example: "November 15-22, 2024, business hours only (9 AM - 5 PM EST)"

DISCOVERED TECHNOLOGY STACK:
Provide what you've identified through reconnaissance:

Frontend Technology:
🏢 Enterprise: "React 18.2, TypeScript, Material-UI components"
🌐 Consumer: "Modern JavaScript framework, component library"

Backend Technology:
🏢 Enterprise: "Node.js 18 with Express framework"
🌐 Consumer: "REST API, [language/framework if known]"

Authentication:
🏢 Enterprise: "JWT tokens with Auth0 integration, optional MFA"
🌐 Consumer: "Token-based authentication with SSO"

Database:
🏢 Enterprise: "PostgreSQL 14"
🌐 Consumer: "Relational database"

Known Third-Party Services:
🏢 Enterprise: "Auth0 (authentication), Stripe (payments - OUT OF SCOPE), AWS S3 (file storage)"
🌐 Consumer: "[List any identified integrations]"

APPLICATION FEATURES DISCOVERED:
List the functionality you've mapped:

User Features:
- [Feature 1]: Example: "User registration and login"
- [Feature 2]: Example: "Profile management with photo upload"
- [Feature 3]: Example: "Search functionality for records"
- [Feature 4]: Example: "Secure messaging between users"
- [Continue with your discovered features...]

Administrative Features (if applicable):
- [Admin Feature 1]: Example: "User management (create/edit/delete accounts)"
- [Admin Feature 2]: Example: "System configuration settings"
- [Continue with admin features...]

API ENDPOINTS IDENTIFIED:
List discovered endpoints from reconnaissance:

Authentication Endpoints:
- POST /api/v1/auth/login
- POST /api/v1/auth/register
- [Your discovered auth endpoints...]

Data Access Endpoints:
- GET /api/v1/users/me
- GET /api/v1/records
- GET /api/v1/records/:id
- [Your discovered data endpoints...]

File Handling Endpoints:
- POST /api/v1/upload
- GET /api/v1/files/:id
- [Your discovered file endpoints...]

[Continue with other endpoint categories you've found...]

INITIAL OBSERVATIONS:
Note anything unusual or interesting you've observed:

Potential Concerns:
- [Observation 1]: Example: "Record IDs appear to be sequential integers"
- [Observation 2]: Example: "No rate limiting observed on login endpoint"
- [Observation 3]: Example: "Verbose error messages may leak information"
- [Your observations...]

Questions I Have:
- [Question 1]: Example: "How should I test authorization between user roles?"
- [Question 2]: Example: "What injection types are most relevant for this stack?"
- [Your questions...]

TASK FOR AI:
Based on the above context, help me:

1. Identify potential vulnerability categories most relevant to this application and technology stack
2. Prioritize testing areas based on:
   - Likelihood of finding issues
   - Potential business impact if vulnerabilities exist
   - Common weaknesses in the identified technologies
3. Suggest specific test cases for the TOP 3-5 highest-priority areas
4. Flag any endpoints or features that warrant extra attention based on their functionality

Structure your response by vulnerability category (e.g., Authorization Issues, Injection Flaws, etc.) and for each category provide:
- Why it's relevant to this application
- Which features/endpoints to test
- What to look for specifically
- Suggested testing approach

Do NOT provide:
- Generic vulnerability lists
- Testing techniques for out-of-scope items
- Exploitation code (I'm in planning phase)
- Assumptions about features I haven't discovered

Focus on helping me develop a focused, efficient testing strategy within my authorized scope.
```

---

**USING THE AI RESPONSE:**

After the AI provides analysis, you should:

**1. VALIDATE THE SUGGESTIONS AGAINST YOUR SCOPE:**
- Does each suggested test stay within authorized boundaries?
- Are the identified priorities aligned with client concerns?
- Are there any suggested tests that require additional authorization?

**2. REFINE WITH FOLLOW-UP PROMPTS (Iteration):**

If the AI's response is too generic, create a more specific follow-up:

```markdown
Your analysis identified [SPECIFIC CATEGORY] as high priority. I want to focus specifically on testing [SPECIFIC FEATURE] for [SPECIFIC VULNERABILITY TYPE].

Given that:
- [Specific technical detail about the feature]
- [Specific constraint or observation]
- [Specific authorization boundary]

Provide a detailed testing methodology for just this one area, including:
- Specific test cases with example inputs
- What responses to look for
- How to distinguish vulnerability from expected behavior
- Red flags that would indicate this is worth deeper investigation
```

**3. CREATE SEPARATE TESTING PROMPTS:**

For each high-priority area identified, create a NEW focused prompt for actual testing:

Example: If AI identified "Authorization bypass" as priority, create a separate prompt:
```markdown
I am now actively testing authorization controls for [SPECIFIC FEATURE]. 

[Provide specific context about the feature, endpoints, and what you're trying to test]

I need help [specific testing assistance request].
```

This keeps each testing phase focused and prevents context overload.

---

**VERIFICATION CHECKLIST:**

Before proceeding with testing based on AI suggestions:

- [ ] All suggested tests are within authorized scope
- [ ] I understand WHY each area is a priority (not just accepting AI's word)
- [ ] I have test accounts/credentials needed for suggested tests
- [ ] I've confirmed testing methods won't violate "prohibited actions"
- [ ] I know how to verify if something is a true vulnerability vs. expected behavior

---

**ITERATION GUIDANCE:**

**If AI response is too broad:**
- Pick ONE vulnerability category from its list
- Create a new prompt focused solely on that category
- Provide more specific technical details about the relevant features

**If AI response assumes technologies you don't have:**
- Clarify: "I don't have [X], I have [Y] instead"
- Ask: "How does this change your analysis?"

**If AI suggests out-of-scope testing:**
- Remind it of scope boundaries
- Ask: "Given that [X] is out of scope, what alternatives focus on authorized areas?"

**If you discover new features mid-engagement:**
- Run this prompt again with updated features list
- Ask: "How do these new discoveries change testing priorities?"

---

**COMMON MISTAKES TO AVOID:**

❌ **Using AI output directly without validation**
- AI may suggest tests that violate your scope
- Always verify suggestions against your authorization

❌ **Providing sensitive client data in prompts**
🏢 Enterprise AI: Real data OK with proper DPA
🌐 Consumer AI: Sanitize/genericize all client details

❌ **Asking for exploitation code in planning phase**
- This prompt is for ANALYSIS and PLANNING
- Exploitation assistance should be separate, focused prompts

❌ **Accepting generic "test for SQL injection" advice**
- Push for specificity: WHERE to test, WHY it's likely, HOW given your tech stack

❌ **Trying to cover entire pentest in one prompt**
- Break testing into phases: reconnaissance → analysis (this prompt) → testing (separate prompts) → exploitation (more prompts) → reporting

---

**EXAMPLE WORKFLOW:**

1. **Use this prompt** → Get prioritized vulnerability areas
2. **Review AI output** → Validate against scope, refine priorities
3. **Create focused testing prompts** → One prompt per vulnerability category you're actively testing
4. **Test and document** → Manual testing with AI assistance for specific challenges
5. **Create exploitation prompts** → If you find vulnerabilities, get AI help with PoC development (separate prompt)
6. **Create reporting prompts** → After testing complete, get AI help documenting findings (separate prompt)

Each phase = separate prompt with relevant context for that phase.

---

### Prompt 2: Vulnerability Reproduction and Impact Analysis

**When to use this:** You've discovered what appears to be a vulnerability during testing and need to thoroughly validate it's real, understand its full impact, and prepare documentation for your client.

**Why this is a separate prompt:** Reproduction and impact analysis requires different context than discovery. You're no longer exploring - you're validating and documenting. This prompt helps you think through verification rigorously before reporting.

**Four Principles Application:**
- **Context:** You provide specific vulnerability details, testing evidence, and client environment
- **Specificity:** You describe the EXACT behavior observed, not generic "I found XSS"
- **Structure:** The prompt guides you through validation → impact → remediation → documentation
- **Iteration:** Start with validation, iterate based on findings, create follow-up prompts for deeper analysis if needed

---

**⚠️ VALIDATION REMINDER**

Before reporting a vulnerability to your client:
- [ ] Reproduced at least 3 times consistently
- [ ] Confirmed it's not expected behavior (check docs/client)
- [ ] Assessed actual impact (not theoretical maximum)
- [ ] Stayed within authorized testing boundaries
- [ ] Collected sanitized evidence (no real data in screenshots)

---

**STARTER PROMPT TEMPLATE:**

```markdown
I am conducting an authorized penetration test and have discovered what appears to be a vulnerability. I need help thoroughly validating this finding, assessing its real-world impact, and preparing accurate documentation for my client.

ENGAGEMENT CONTEXT:
Client: [YOUR_CLIENT]
🏢 Enterprise: "HealthTech Solutions Inc."
🌐 Consumer: "Authorized client"

Application: [APPLICATION]
🏢 Enterprise: "PatientPortal v3.2 at staging.patientportal.example.com"
🌐 Consumer: "[Application under test]"

Testing Authorization: [REFERENCE]
🏢 Enterprise: "Contract #PT-2024-156, approved testing Nov 15-22"
🌐 Consumer: "Authorized engagement with written approval"

DISCOVERED VULNERABILITY:

Vulnerability Type: [CATEGORY]
Examples: "Insecure Direct Object Reference (IDOR)", "SQL Injection", "Cross-Site Scripting (XSS)", "Authentication Bypass"

Affected Component: [SPECIFIC LOCATION]
🏢 Enterprise: "GET /api/v1/records/:id endpoint"
🌐 Consumer: "[Specific endpoint, page, or feature]"

Discovery Date: [WHEN]
Discovery Method: [HOW YOU FOUND IT]
Example: "Manual testing of authorization controls using Burp Suite Repeater"

OBSERVED BEHAVIOR:

What I Did (Step-by-step):
1. [Step 1]
   Example: "Logged in as standard_user@test.com (user ID: 1234)"
2. [Step 2]
   Example: "Accessed my own record at /api/v1/records/1234 - successful"
3. [Step 3]
   Example: "Modified URL parameter to /api/v1/records/5678 (different user's ID)"
4. [Step 4]
   Example: "Received HTTP 200 OK with full record data belonging to user 5678"

Expected Behavior:
[What SHOULD happen]
Example: "Should receive HTTP 403 Forbidden or 404 Not Found when attempting to access another user's record"

Actual Behavior:
[What ACTUALLY happened]
Example: "Received HTTP 200 OK with complete record data including sensitive information (name, email, medical history) belonging to a different user"

Evidence Collected:
- [Evidence type 1]: Example: "HTTP request/response saved in Burp Suite"
- [Evidence type 2]: Example: "Screenshot showing response with different user's data"
- [Evidence type 3]: Example: "Video recording of reproduction steps"

Reproduction Consistency:
[How reliably can you reproduce this?]
Example: "Successfully reproduced 5/5 attempts with different user IDs"

TECHNICAL DETAILS:

Request Details:
```
[Paste actual HTTP request - sanitized]

Example:
GET /api/v1/records/5678 HTTP/1.1
Host: staging.patientportal.example.com
Authorization: Bearer eyJhbGc... [JWT token]
User-Agent: Mozilla/5.0
Accept: application/json
```

Response Details:
```
[Paste actual HTTP response - sanitized]

Example:
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": 5678,
  "user_id": "different-user-uuid",
  "name": "Different User",
  "email": "different@example.com",
  [sensitive data fields...]
}
```

Authentication Context:
[What authentication was used?]
Example: "JWT token belonging to user 1234, no admin privileges"

MY INITIAL IMPACT ASSESSMENT:

What Data Can Be Accessed:
- [Data type 1]: Example: "All user profile information"
- [Data type 2]: Example: "Medical history and records"
- [Data type 3]: Example: "Personal identifying information (PII/PHI)"

What Actions Can Be Performed:
- [Action 1]: Example: "Read any user's records"
- [Action 2]: Example: "Potentially enumerate all users by iterating IDs"
- [Action 3]: Example: "Download attached medical documents"

Apparent Scope:
[How widespread is this?]
Example: "Appears to affect all /api/v1/records/* endpoints. Tested on 10 random user IDs, all accessible."

MY QUESTIONS FOR VALIDATION:

1. [Validation question 1]
   Example: "Is this actually a vulnerability or could this be intentional 'admin view' functionality?"

2. [Validation question 2]
   Example: "What's the realistic attack scenario - who would exploit this and how?"

3. [Validation question 3]
   Example: "What additional testing should I do to fully understand the scope?"

4. [Impact question 1]
   Example: "How do I assess the business impact accurately without exaggerating?"

5. [Remediation question 1]
   Example: "What's the proper fix for this type of vulnerability?"

TASK FOR AI:

Help me thoroughly validate and analyze this finding by:

1. **Validation Questions:**
   - Is this definitely a vulnerability or could it be expected behavior?
   - What additional tests would confirm this is exploitable?
   - Are there edge cases or scenarios I should test?
   - What would a false positive look like for this type of issue?

2. **Impact Analysis:**
   - What's the realistic worst-case scenario if exploited?
   - Who could exploit this (attacker profiles)?
   - What's the actual business impact (not just technical impact)?
   - What compliance/regulatory implications exist?

3. **Remediation Guidance:**
   - What's the proper technical fix for this vulnerability?
   - Are there multiple remediation approaches?
   - What should I recommend to the client?

4. **Documentation Preparation:**
   - How should I structure this finding in my report?
   - What evidence is most important to include?
   - How do I explain this clearly to both technical and non-technical audiences?

Do NOT:
- Assume this is definitely a critical issue without proper validation
- Suggest testing that goes beyond my authorized scope
- Recommend exploitation beyond what I've already done for proof-of-concept
- Exaggerate impact for dramatic effect

Focus on helping me be thorough, accurate, and professional in my assessment.
```

---

**USING THE AI RESPONSE:**

**1. VALIDATION PHASE:**

AI will likely suggest additional validation tests. Before performing them:

```markdown
SCOPE CHECK:
For each suggested validation test:
- [ ] Is this within my authorized scope?
- [ ] Is this safe to perform in the client's environment?
- [ ] Do I need additional client approval?
- [ ] What's the worst-case impact if something goes wrong?
```

**2. IMPACT ASSESSMENT REFINEMENT:**

If AI's impact analysis seems theoretical or exaggerated:

**Follow-up prompt:**
```markdown
You suggested [IMPACT SCENARIO]. However, I need to assess REALISTIC impact for this specific client.

Client Context:
- Industry: [Healthcare/Finance/etc.]
- Data handled: [Specific types]
- User base: [Approximate size]
- Regulatory requirements: [HIPAA/PCI-DSS/etc.]

Given this context:
- What's the REALISTIC (not theoretical maximum) impact?
- How would I quantify the risk for THIS client specifically?
- What compliance violations would THIS client face?
- How do I explain impact without fear-mongering?
```

**3. REMEDIATION VERIFICATION:**

Before recommending fixes to client, verify they're practical:

**Follow-up prompt:**
```markdown
You suggested [REMEDIATION APPROACH]. I need to ensure this recommendation is:

1. Technically accurate for their stack: [Their specific tech]
2. Practical to implement (not a complete rewrite)
3. Doesn't break existing functionality
4. Addresses the root cause, not just symptoms

Can you provide:
- Specific code examples for [their framework/language]
- Verification steps to confirm the fix works
- Potential side effects or considerations
- Alternative approaches if the primary fix is too complex
```

**4. FALSE POSITIVE CHECK:**

Always validate with AI whether this could be expected behavior:

**Follow-up prompt:**
```markdown
Before I report this as a vulnerability, help me rule out false positive scenarios:

Could this behavior be:
- Intentional functionality for [specific use case]?
- Proper behavior given [context I might be missing]?
- Documented feature I'm unaware of?

How can I confirm with the client whether this is expected without revealing the vulnerability details if it's not?

Suggested questions to ask client:
[Draft non-revealing questions to validate expected behavior]
```

---

**VERIFICATION CHECKLIST:**

Before documenting this in your report:

**Validation:**
- [ ] Reproduced minimum 3 times consistently
- [ ] Tested with multiple user accounts/roles
- [ ] Confirmed it's not documented/expected behavior
- [ ] Tested edge cases suggested by AI
- [ ] Ruled out false positive scenarios

**Impact Assessment:**
- [ ] Realistic impact identified (not just theoretical)
- [ ] Specific data at risk quantified
- [ ] Client-specific compliance implications understood
- [ ] Attack scenarios are plausible for this client

**Evidence:**
- [ ] Complete HTTP requests/responses captured
- [ ] Screenshots/videos recorded
- [ ] All evidence sanitized (no real client data)
- [ ] Evidence clearly demonstrates the vulnerability

**Remediation:**
- [ ] Fix is technically accurate
- [ ] Fix is practical for client to implement
- [ ] Verification steps are clear
- [ ] Alternative approaches considered

**Documentation:**
- [ ] Finding is explained clearly
- [ ] Both technical and business impact articulated
- [ ] Remediation guidance is specific and actionable
- [ ] Report-ready format drafted

---

**ITERATION GUIDANCE:**

**If AI suggests unrealistic impact:**
- Push back: "That seems exaggerated for this context. What's REALISTIC impact?"
- Provide more client context to ground the analysis

**If remediation seems too complex:**
- Ask: "What's a simpler fix that addresses the immediate risk?"
- Request: "Phased approach: quick fix now, comprehensive fix later?"

**If you're uncertain about severity:**
- Use CVSS calculator with AI help: "Walk me through CVSS scoring for this"
- Compare to similar vulnerabilities: "How does this compare to [similar CVE]?"

**If client questions your finding:**
- Create evidence package: "Help me create a clear demonstration that shows [X]"
- Prepare FAQ: "What questions might client ask about this finding?"

---

**COMMON MISTAKES TO AVOID:**

❌ **Reporting before thorough validation**
- One reproduction isn't enough - verify consistency
- Could be race condition, timing issue, or misunderstanding

❌ **Exaggerating impact for severity inflation**
- "Could lead to" ≠ "does lead to"
- Theoretical maximum ≠ realistic scenario
- Client loses trust if impacts are overblown

❌ **Generic remediation advice**
- "Fix authorization" is not helpful
- Provide specific code examples or configuration changes

❌ **Testing beyond scope during validation**
- Just because you found a vulnerability doesn't mean unlimited testing
- Each validation test must still be within authorization

❌ **Including real client data in documentation**
- Sanitize everything: emails, names, IDs, sensitive data
- Use test data or placeholders in evidence

❌ **Assuming AI's severity rating is correct**
- AI doesn't understand your client's specific context
- YOU assess severity based on real business impact

---

**EXAMPLE WORKFLOW:**

1. **Discover potential vulnerability** during testing
2. **Use this prompt** → Get validation guidance and impact analysis
3. **Perform suggested validation tests** → Confirm it's real
4. **Refine impact assessment** → Follow-up prompts for realistic impact
5. **Verify remediation guidance** → Ensure fix is practical
6. **Document finding** → Prepare for client report (may use separate reporting prompt)
7. **Client discussion** → Present finding with confidence backed by thorough analysis

---

**WHEN TO CREATE FOLLOW-UP PROMPTS:**

**Create a NEW prompt if:**
- You need to explore a different attack vector based on this finding
- You want to develop a proof-of-concept exploit (separate exploitation prompt)
- You need help explaining this to non-technical stakeholders (separate communication prompt)
- Client requests more detail on specific aspect (focused follow-up prompt)

**Continue iterating THIS prompt if:**
- You need clarification on AI's validation suggestions
- You're refining the impact assessment
- You're adjusting remediation recommendations
- You're preparing different versions of the finding description
