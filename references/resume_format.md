# Resume Format

Version: 2026-06-25

Use this format for the resume so the Word document stays clean, compact, and recruiter-friendly.

The resume must be human-readable first. ATS compatibility and concision matter, but they should not flatten the meaning of the work or turn accomplishments into jargon.

## Page Setup

- Use a standard US Letter page.
- Use 0.5 inch margins on all sides.
- Use a clean professional font such as Arial, Calibri, or Aptos.
- Use 10-11 pt body text.
- Keep spacing tight and consistent.
- Avoid large blank gaps between sections.
- Target 1-2 pages.
- Use 2 pages maximum, but the second page must be earned by strong, relevant accomplishments.
- Submit as PDF by default unless the employer explicitly requests `.docx`.

## File Workflow

- Maintain the resume source as Markdown whenever possible.
- Create or preserve a session `source_resume.md` file before editing.
- Treat the source resume as the source of truth for all revisions.
- Generate `.docx` or PDF outputs only after the Markdown content is reviewed and approved by the user.
- Use the approved Markdown resume as the only content source for final document generation.
- Do not manually add new resume claims directly in the `.docx` unless the same claim is also supported by the source resume.
- Keep output filenames aligned with the source or session name so it is clear which Markdown file produced each Word or PDF file.

## Header

- Center the candidate name at the top.
- Make the name the largest text on the page, around 18 pt.
- Put contact details on one centered line below the name.
- Separate contact items with vertical bars.
- Use standard hyperlink styling for email and LinkedIn: blue, underlined, and clickable.
- Keep visible URLs clean, such as `linkedin.com/in/username` instead of a long tracking URL.
- Include:
  - Email
  - Phone number
  - LinkedIn URL
  - Location

Example:

```text
Candidate Name
email@example.com | (555) 555-5555 | linkedin.com/in/username | City, State
```

## Section Headings

- Use uppercase section headings.
- Make section headings bold.
- Add a thin horizontal line under each section heading.
- Keep section heading spacing compact.

Required sections:

- EXPERIENCE
- EDUCATION
- SKILLS

Optional sections if relevant:

- SUMMARY
- PROJECTS
- CERTIFICATIONS
- PUBLICATIONS

## Summary Section

Use a summary only when it helps position the resume for a specific target role.

Include a summary when:

- The target role needs immediate framing, such as Staff Engineer, Senior Platform Engineer, Security Engineer, or Infrastructure Engineer.
- The resume spans multiple domains and needs a clear positioning statement.
- The first experience section is dense and needs a short preview of the candidate's strongest themes.

Skip the summary when:

- The resume is already too long.
- The first role clearly communicates the target profile.
- The summary would repeat generic claims that are not backed by the experience section.

Formatting rules:

- Place SUMMARY between the header and EXPERIENCE.
- Keep it to 2-3 sentences maximum.
- Make it specific to the target role.
- Mention the strongest technical themes, scope, and business/security impact.
- Avoid generic phrases such as "results-driven", "passionate", or "team player".
- Use plain language before keywords. A hiring manager should understand the candidate's specialty without needing to decode a string of acronyms.
- Do not pack too many concepts into one sentence. If the sentence contains more than 2-3 dense technical terms, simplify it.

Good summary pattern:

```text
Senior software engineer focused on cloud infrastructure, distributed systems, and platform reliability. Led large-scale migrations across hundreds of services, reducing operational risk, improving service reliability, and simplifying adoption for engineering teams.
```

Better human-readable summary pattern:

```text
Software engineer focused on secure cloud infrastructure and distributed services. Led migrations that moved large application fleets away from shared credentials and manual operational processes toward safer, automated platform patterns, reducing risk and engineering overhead.
```

## Experience Section

Each company should use this structure:

```text
Company Name
Role Title                                                    Date Range
- Impact bullet
  - Supporting detail, if needed
```

Formatting rules:

- Company name should be bold and slightly larger than body text.
- Role title should be bold.
- Date range should be right-aligned on the same line as the role title.
- Use reverse chronological order.
- Keep each bullet focused on impact, scale, ownership, or technical depth.
- Start bullets with strong action verbs.
- Include measurable results when available.
- Avoid too many nested bullets; use them only when a major accomplishment needs supporting implementation details.

Bullet formula:

```text
Action verb + what was built or changed + scale/context + outcome
```

Human-readable bullet formula:

```text
Problem or context + what you built or changed + why it mattered
```

Use this version when the work is technically complex. It is better for a bullet to be slightly longer and clear than short and cryptic.

Examples of useful bullet ingredients:

- Action: Led, architected, migrated, redesigned, automated, implemented, launched.
- What changed: Authentication model, deployment pipeline, SDK, control plane, API, data platform, reliability workflow.
- Scale/context: Hundreds of services, millions of requests, multiple customer teams, high-throughput platform, multi-tenant system.
- Outcome: Reduced risk, lowered operational overhead, saved cost, improved reliability, reduced incidents, enabled adoption.

Good bullet pattern:

```text
- Led migration of hundreds of services from shared credentials to per-service identities, reducing security risk and eliminating manual credential rotation.
```

Better human-readable bullet pattern:

```text
- Led the transition from shared service credentials to isolated per-application identities, reducing the impact of a compromised token or misconfigured service.
```

## Human Readability Rules

Use these rules when editing resume content, especially for complex platform, security, identity, or distributed systems work.

- Preserve the original meaning before shortening anything.
- Explain why the work mattered, not just what technology was used.
- Keep the cause-and-effect relationship visible: what was risky or inefficient, what changed, and what improved.
- Do not compress several distinct projects into one generic bullet.
- Split a complex accomplishment into separate bullets when each bullet proves a different kind of impact.
- Use connecting phrases such as "allowing", "removing the need for", "reducing", "eliminating", or "so that" when they clarify the result.
- Define or expand uncommon acronyms on first use when space allows.
- Avoid sentences that stack many unexplained terms together, such as several acronyms, platform names, and internal system names in one line.
- Keep concrete details that make the work understandable, such as the prior risk, migration size, request volume, customer scope, zero-downtime constraint, or operational burden removed.
- Avoid vague impact phrases unless they are tied to a specific result. For example, "improved security posture" is weak by itself; "removed the ability for one application to request tokens on behalf of another" is stronger.
- Human readability beats keyword density. Keywords should support the story, not replace it.

Before accepting a rewritten bullet, ask:

- Would someone outside the immediate team understand what changed?
- Does the bullet explain the risk, system, or business reason behind the work?
- Is the outcome concrete enough to justify keeping the bullet?
- Did the edit remove important context just to make the bullet shorter?

Avoid:

- Bullets that are too long.
- Dense paragraphs disguised as bullets.
- Repeating the same achievement in multiple bullets.
- More than 5 bullets under one role unless the role is the main target experience.

What to cut:

- Cut or rewrite any bullet that does not include at least one of:
  - A number or scale marker.
  - A named technology, platform, or system.
  - A clear outcome or impact.
- Cut bullets that only describe normal job responsibilities.
- Cut implementation details that do not help prove scope, ownership, technical depth, or impact.
- Cut repeated security claims unless each one proves a different result.
- Prefer one strong end-to-end accomplishment over several smaller bullets about the same project.
- Do not cut context that explains why the accomplishment matters. If removing context makes the bullet harder to understand, rewrite it instead of cutting it.
- Do not cut all supporting details from complex security or infrastructure work. Keep enough detail to make the achievement credible.

## Editing Workflow

Use this order when revising the resume:

1. Preserve the factual meaning of the original bullet.
2. Identify the problem, action, scale, and outcome.
3. Remove repetition across bullets.
4. Rewrite in plain language.
5. Add technical terms only where they make the accomplishment more specific.
6. Check that the bullet still makes sense to a technical hiring manager who did not work on the system.
7. Only then tighten wording for length.

## Education Section

Each degree should use this structure:

```text
School Name                                                  Graduation Date
Degree, Major, GPA if strong
```

Formatting rules:

- School name should be bold.
- Graduation date should be right-aligned.
- Include GPA only when it is strong and useful.

## Skills Section

Group skills by category.

Use this structure:

```text
Languages: Java, C#, Python, PowerShell, SQL
Concepts: Distributed Systems, RESTful APIs, CI/CD, DevOps, Test-Driven Development
```

Formatting rules:

- Category labels should be bold.
- Keep skills relevant to the target role.
- Avoid overly broad or low-signal skills.
- Prefer concrete technologies and engineering concepts.

## ATS Compatibility

Keep the resume easy for applicant tracking systems to parse.

- Keep all resume text in the main document body.
- Avoid text boxes, floating shapes, icons, columns, headers, and footers for important content.
- Avoid tables for layout unless absolutely necessary.
- Use standard Word bullet lists or simple text bullets.
- Use common section names such as EXPERIENCE, EDUCATION, and SKILLS.
- Use standard date ranges, such as `January 2022 - Present`.
- Do not rely on color, icons, or visual placement to communicate important information.
- Keep company names, role titles, dates, schools, degrees, and skills as real selectable text.
- Test the resume by copying all text from the PDF or Word document into a plain text file; the order should still make sense.

## Content Guidelines

- Prioritize accomplishments over responsibilities.
- Show scope using numbers where possible.
- Make security, scale, reliability, and cost impact explicit.
- Keep bullets concise enough to scan quickly.
- Use present tense for current work and past tense for previous work.
- Use consistent punctuation and date formats.
- Keep terminology consistent, such as choosing either a full product name or its acronym after first use.

## Tailoring Notes

For each target resume, identify the strongest themes before editing. Examples:

- Cloud infrastructure and distributed systems
- Security, identity, or authentication architecture
- Reliability, incident reduction, and operational excellence
- Developer platforms, SDKs, and internal tooling
- Large-scale migrations across services, applications, or teams
- Cost reduction, performance improvement, or capacity expansion
- Customer-facing product delivery or cross-functional launch work

The most relevant recent role should usually receive the most space, but it still needs to be easy to scan. Older or less relevant roles should be shorter and focused on transferable accomplishments.
