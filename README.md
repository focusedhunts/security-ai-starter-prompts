# Security AI Starter Prompts

**Professional-grade prompt frameworks for cybersecurity operations**

---

## About This Repository

This repository provides starter prompts for security professionals integrating AI tools into their workflows. These prompts are designed as **customizable frameworks** rather than copy-paste templates, reflecting the reality that effective AI use in security requires adaptation to your specific context, constraints, and operational environment.

This collection serves as a practical companion to the book [**Prompt Intelligence: An AI Framework for Security Professionals**](https://github.com/focusedhunts/security-ai-starter-prompts) by Joe Schumacher, implementing the principles and approaches detailed in the text.

---

## The Four Principles Framework

All prompts in this repository are built on four foundational principles that distinguish professional AI use from casual experimentation:

### 1. **Context is King**
Effective prompts provide appropriate context about your role, environment, and constraints without compromising sensitive information. Security work demands more contextual specificity than most domains; generic prompts produce generic (and often dangerous) outputs.

### 2. **Specificity Drives Accuracy**
Vague requests yield vague results. Professional prompts define precise requirements across three dimensions: format (how information should be structured), scope (what's included and excluded), and depth (the appropriate detail level for your audience and purpose).

### 3. **Structure Enables Clarity**
Complex security tasks benefit from structured approaches that break work into discrete phases, separate analytical from synthetic work, and specify output organization. Structure transforms AI from a conversational tool into a directed capability.

### 4. **Iteration Reveals Truth**
First attempts rarely produce final deliverables in security work. Systematic iteration, whether through multi-turn conversations or prompt refinement, progressively improves outputs while building your understanding of both the problem and the AI's capabilities.

---

## Repository Structure

This repository organizes prompts by **operational role** rather than by specific tools or technologies, recognizing that security professionals think in terms of operational mindsets and workflows:

```
├── governance/          # GRC, compliance, policy, and risk management
├── defensive/           # SOC, detection, incident response, and threat hunting  
├── offensive/           # Red team, penetration testing, and security research
└── README.md           # This file
```

Each directory contains:
- **Role-specific prompt frameworks** organized by common tasks
- **Customization guidance** for adapting prompts to your context
- **Verification checklists** appropriate to each operational domain
- **Usage notes** explaining when prompts work well and when they don't

---

## Important: These Are Starting Points, Not Solutions

**Critical Understanding**: The prompts in this repository are **starter frameworks** designed for customization, not finished templates for direct use. Here's why:

- **Your context matters**: Security environments vary dramatically. What works for a healthcare SOC analyst differs from what works for a financial services detection engineer. Effective prompts encode your specific organizational context, technical environment, and operational constraints.

- **Sensitivity requires adaptation**: These prompts use generic placeholders and sanitized examples. You must adapt them to protect your organization's sensitive information while providing enough context for useful outputs.

- **Verification is mandatory**: Every AI output requires verification appropriate to its stakes. These prompts include verification guidance, but you remain responsible for ensuring accuracy, completeness, and appropriateness before operational use.

- **Skills develop through practice**: Using these prompts effectively requires developing judgment about context provision, specificity calibration, and iteration strategies. The prompts accelerate your learning but don't replace it.

**If you treat these as copy-paste solutions, they will fail.** If you use them as foundations for building prompts suited to your specific situation, they will accelerate your work significantly.

---

## Who Should Use This Repository

This repository serves security professionals across roles and experience levels:

- **Governance and Compliance**: GRC analysts, compliance officers, risk managers, auditors, and policy writers seeking to accelerate framework mapping, control documentation, and compliance reporting

- **Defensive Operations**: SOC analysts, detection engineers, incident responders, threat hunters, and security engineers working to improve alert triage, detection logic development, and investigation workflows

- **Offensive Security**: Red team operators, penetration testers, and security researchers conducting authorized assessments and requiring assistance with reconnaissance, reporting, and operational planning

All prompts assume you're operating within appropriate legal and ethical boundaries. Offensive security prompts are intended exclusively for authorized security assessments conducted under proper contracts and scope agreements.

---

## Getting Started

1. **Read the relevant chapter** in *Prompt Intelligence* for your operational role (Chapters 10-12) to understand the principles and boundaries that make these prompts effective

2. **Review the directory** matching your primary security function to understand the available prompt categories

3. **Select a prompt framework** for a specific task you perform regularly

4. **Customize systematically**:
   - Replace placeholder context with your actual environment details (sanitized appropriately)
   - Adjust specificity to match your output requirements
   - Modify structure to align with your workflows
   - Plan verification steps appropriate to the stakes

5. **Document what works**: Capture your customizations, note what verification catches, and build your personal or team prompt library over time

6. **Iterate and improve**: Refine prompts based on output quality, verification findings, and operational experience

---

## AI Tool Selection Considerations

The effectiveness of these prompts depends partly on using appropriate AI tools for your security work:

- **Enterprise vs. Consumer Tools**: Prompts involving organizational data, control implementations, or risk assessments should use enterprise AI tools with proper data processing agreements, not consumer services

- **Data Sensitivity**: Match tool selection to information sensitivity. Public research uses different tools than sanitized operational data, which uses different tools than highly sensitive analysis (which may require no AI assistance)

- **Verification Requirements**: Higher-stakes outputs demand more rigorous verification regardless of tool choice. The prompts include verification guidance, but you determine appropriate rigor for your context

Consult Chapter 4 (*The Security Professional's AI Toolkit*) for detailed guidance on tool selection and data protection strategies.

---

## Boundaries and Limitations

These prompts operate within clear boundaries established throughout *Prompt Intelligence*:

**When AI Assistance Helps**:
- Pattern recognition across large volumes of data
- Draft generation for routine documentation
- Framework mapping and compliance synthesis  
- Research and learning acceleration
- Query and detection logic development
- Timeline construction and event correlation

**When AI Assistance Fails or Is Inappropriate**:
- Real-time decisions during active incidents
- Risk acceptance or other formal decisions requiring accountability
- Legal interpretation of regulations or contractual obligations
- Ethical judgment about surveillance, privacy, or competing values
- Real-time systems requiring deterministic behavior
- Evidence documentation subject to legal scrutiny
- Highly sensitive information that cannot be safely sanitized

Understanding these boundaries prevents applying AI where it fundamentally cannot succeed or where its use introduces unacceptable risk.

---

## Contributing

We welcome contributions that improve prompt effectiveness, expand coverage, or share lessons learned. When contributing:

- **Maintain the principles**: Ensure prompts reflect context, specificity, structure, and iteration
- **Provide customization guidance**: Help others adapt prompts to their situations
- **Include verification checklists**: Specify what validation is essential before operational use
- **Document limitations**: Note where prompts work well and where they struggle
- **Sanitize examples**: Use generic placeholders rather than actual organizational details

See `CONTRIBUTING.md` for detailed guidelines.

---

## License

This repository is licensed under the MIT License. See `LICENSE` for details.

---

## Acknowledgments

These prompts emerged from systematic experimentation with AI tools across diverse security contexts, refined through both successes and failures. They represent patterns that consistently produce professional-grade outputs when properly customized and verified.

Special thanks to the security practitioners who provided feedback on early versions and helped identify common pitfalls that the current frameworks help avoid.

---

## Additional Resources

- **Book**: [*Prompt Intelligence: An AI Framework for Security Professionals*](link-to-book) - Comprehensive guide to the principles, techniques, and professional considerations underlying these prompts

- **Author**: [Joe Schumacher](https://focusedhunts.com) - Founder/Principal, Focused Hunts, LLC

- **Discussions**: Open an issue or discussion in this repository to share experiences, ask questions, or propose improvements

---

## Getting Help

If you're struggling to adapt these prompts effectively:

1. **Review the relevant book chapter** - Most challenges stem from missing context, insufficient specificity, or unclear structure that the book addresses directly

2. **Check the verification guidance** - Many issues surface during proper verification, which these prompts help structure

3. **Start simpler** - If a complex prompt isn't working, break it into smaller phases and build up systematically

4. **Share your experience** - Open a discussion describing what you're trying to accomplish, what's not working, and what you've tried. The community learns from these conversations.

---

**Remember**: These prompts don't replace your security expertise—they augment it. You remain responsible for verification, judgment, and outcomes. Use them thoughtfully, adapt them systematically, and always maintain the professional standards your work demands.
