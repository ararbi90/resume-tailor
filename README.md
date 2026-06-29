# resume-tailor

Resume tailoring skill for formatting resumes, tailoring them to job descriptions, and verifying that revised content stays grounded in the original resume source of truth.

## What It Does

`resume-tailor` helps an AI assistant take a resume from Markdown, Word-extracted text, PDF-extracted text, or pasted text and either:

- Format it into a clean, human-readable, ATS-safe resume.
- Tailor it to a specific job posting.
- Identify strengths, gaps, and weak evidence against a job description.
- Verify that revised resume claims are supported by the original resume.

The original resume must always be preserved as `source_resume.md` and treated as the source of truth. The assistant must not invent experience, titles, dates, technologies, metrics, certifications, or outcomes.

## Repository Layout

```text
resume-tailor/
├── SKILL.md
├── references/
│   └── resume_format.md
└── platforms/
    ├── claude.md
    ├── codex.md
    └── copilot.md
```

## Core Workflow

1. Give the assistant a resume as a file or pasted text.
2. The assistant creates a session folder and saves the original resume as `source_resume.md`.
3. The assistant asks whether to format the resume or tailor it to a job description.
4. For tailoring, provide a job posting URL or paste the job description.
5. The assistant extracts requirements, revises only supported resume content, and creates a gap analysis.
6. The assistant creates `claim_verification.md` to map revised claims back to source evidence.
7. Unsupported claims are removed or flagged for user confirmation.
8. After the user approves the revised Markdown content, the assistant creates `final_resume.docx`.

## Using With Codex

Use `SKILL.md` as the Codex skill file.

For local/manual use:

1. Copy or install this folder where Codex can access it.
2. Ask Codex to use the `resume-tailor` skill.
3. Provide a resume file or paste resume text.
4. Codex should read `references/resume_format.md` before rewriting content.
5. Codex should create session files such as:

```text
resume-tailor/sessions/<session>/source_resume.md
resume-tailor/sessions/<session>/formatted_resume.md
resume-tailor/sessions/<session>/tailored_resume.md
resume-tailor/sessions/<session>/gap_analysis.md
resume-tailor/sessions/<session>/claim_verification.md
resume-tailor/sessions/<session>/final_resume.docx
```

The compact Codex prompt is also available at:

```text
platforms/codex.md
```

## Using With Claude

Use the contents of:

```text
platforms/claude.md
```

as Claude project instructions or as the instruction text for a Claude workflow.

Recommended setup:

1. Add `platforms/claude.md` as the main instruction.
2. Add `references/resume_format.md` as supporting project knowledge.
3. Upload or paste the resume.
4. Ask Claude to create `source_resume.md` first.
5. Choose either format-only or job-tailoring mode.

Claude should always produce a claim verification report before finalizing a revised resume.

## Using With Copilot

Use the contents of:

```text
platforms/copilot.md
```

as GitHub Copilot workspace instructions or custom instructions.

Recommended setup:

1. Place this repository in a workspace.
2. Add or reference `platforms/copilot.md` in Copilot instructions.
3. Keep `references/resume_format.md` available in the workspace.
4. Ask Copilot to create a session folder and save the original resume as `source_resume.md`.
5. Ask Copilot to generate Markdown first, then `.docx` or PDF only after the content is reviewed and approved.

## Anti-Fabrication Rule

The job posting is not evidence of candidate experience. It can only guide emphasis and gap analysis.

Every revised claim must be traceable to:

- The original `source_resume.md`, or
- Explicit user-provided additions in the current session.

If a claim cannot be traced, it must be removed or marked as needing user confirmation.
