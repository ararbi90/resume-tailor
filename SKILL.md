---
name: resume-tailor
description: Format, rewrite, or tailor resumes from Markdown, Word documents, PDFs, or pasted text while preserving the original resume as the source of truth. Use when the user asks to improve a resume, convert it into a standard format, tailor it to a job posting or URL, identify gaps against a job description, or produce a revised resume without inventing facts.
---

# Resume Tailor

Use this skill to turn an existing resume into a clean, human-readable, ATS-safe resume or tailor it to a specific job posting. The original resume is always the source of truth.

## Required References

- Read `references/resume_format.md` before formatting or rewriting a resume.
- Read a platform file in `platforms/` only when adapting this workflow for Claude, Codex, or Copilot outside this skill format.

## Core Rules

- Do not invent facts, employers, titles, dates, technologies, metrics, education, certifications, clearances, publications, or outcomes.
- Use only information present in the source resume or explicitly provided by the user during the session.
- Preserve the factual meaning of the source resume before improving wording.
- Prefer human readability over keyword stuffing.
- If the job posting asks for experience not present in the resume, report the gap instead of fabricating coverage.
- After every revision, verify that all new or changed claims are supported by the source resume or user-provided additions.

## Workflow

### 1. Intake The Resume

Accept any of these inputs:

- Markdown file
- Word document (`.docx`; `.doc` if local tooling can read it)
- PDF if text extraction is available
- Pasted resume text

Extract the resume into a Markdown session source file named:

```text
resume-tailor/sessions/<candidate-or-date>/source_resume.md
```

If the candidate name is unknown, use the current date/time or a short neutral session name. Create the session folder if needed.

The `source_resume.md` file is the session source of truth. Do not overwrite it during revision. Write edited versions to separate files such as:

```text
formatted_resume.md
tailored_resume.md
gap_analysis.md
claim_verification.md
final_resume.docx
```

When converting files:

- For Markdown, copy the content into `source_resume.md`.
- For `.docx`, use available local tooling such as `pandoc` or document text extraction.
- For pasted input, save the pasted text as `source_resume.md`.
- If extraction fails, ask the user to paste the resume text.

### 2. Ask For Direction

After the source resume is created, ask:

```text
Do you want me to:
1. Format this resume into the standard resume format, or
2. Tailor it to a job description?
```

Do not tailor to a job until the user chooses option 2 and provides job-posting content.

### 3. Format-Only Path

If the user chooses format-only:

1. Read `references/resume_format.md`.
2. Rewrite the resume into the standard structure while preserving source facts.
3. Improve clarity, section order, bullet readability, and ATS compatibility.
4. Do not add new claims.
5. Produce `formatted_resume.md`.
6. Run the claim verification step.
7. Ask the user to review and approve `formatted_resume.md`.
8. After approval, produce `final_resume.docx` from the approved Markdown using the same structure.

### 4. Tailoring Path

If the user chooses tailoring:

1. Ask for either a job posting URL or pasted job description.
2. If a URL is provided and browsing/fetching is available, read the posting. If not, ask the user to paste it.
3. Save the job posting as:

```text
resume-tailor/sessions/<candidate-or-date>/job_posting.md
```

4. Extract the job requirements into:

```text
resume-tailor/sessions/<candidate-or-date>/job_requirements.md
```

Include:

- Target title
- Required skills
- Preferred skills
- Core responsibilities
- Domain keywords
- Seniority signals
- Missing or unclear requirements

5. Compare the job requirements against `source_resume.md`.
6. Tailor only by emphasizing, reordering, clarifying, and rephrasing supported experience.
7. Produce `tailored_resume.md`.
8. Produce `gap_analysis.md` explaining strengths, weaknesses, and missing evidence.
9. Run the claim verification step.
10. Ask the user to review and approve `tailored_resume.md`.
11. After approval, produce `final_resume.docx` from the approved Markdown using the same structure.

### 5. Gap Analysis

When tailoring to a job, explicitly identify:

- Strong matches supported by the resume.
- Partial matches where the resume shows adjacent experience.
- Gaps where the job asks for something not present in the resume.
- Weak bullets that should be strengthened only if the user can provide evidence.
- Keywords that can be added only if already supported by the resume.

For each gap, say what evidence would be needed. Do not fill the gap yourself.

### 6. Claim Verification

After producing any revised resume, create `claim_verification.md`.

For each new or materially changed bullet, summary sentence, skill, or accomplishment:

```text
Revised claim:
Source evidence:
Status: Supported / Needs user confirmation / Remove
```

Rules:

- Mark a claim `Supported` only if the source resume or user-provided session text clearly supports it.
- Mark a claim `Needs user confirmation` if it is plausible but not explicitly supported.
- Mark a claim `Remove` if it cannot be traced to source evidence.
- Remove or revise unsupported claims before final delivery unless the user explicitly confirms them.
- Do not treat the job posting as evidence of the candidate's experience.

### 7. Final Output

Do not create the final `.docx` until the user has approved the revised Markdown content.

After approval:

1. Use the approved `formatted_resume.md` or `tailored_resume.md` as the only content source for the Word document.
2. Create:

```text
resume-tailor/sessions/<candidate-or-date>/final_resume.docx
```

3. Use the rules in `references/resume_format.md` for margins, font sizing, section structure, date alignment, ATS safety, and human readability.
4. If `pandoc` or another document converter is available, use it. If not, create the `.docx` programmatically or tell the user which local dependency is missing.
5. Do not add, rewrite, or remove resume claims during `.docx` generation. The `.docx` is a formatting output of the approved Markdown content.

When finished, summarize:

- Files created.
- Whether the resume was formatted or tailored.
- Whether `final_resume.docx` was created from approved content.
- Any unsupported claims removed.
- Any gaps or weaknesses found.
- Any user confirmations still needed.

Keep the final message concise and include file links when running in a local workspace.
