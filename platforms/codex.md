# Codex Usage

Codex should use `../SKILL.md` as the canonical skill file.

For manual use outside the skill system, apply this compact workflow:

```text
Use the resume-tailor workflow.

1. Read the user's resume from Markdown, Word-extracted text, PDF-extracted text, or pasted text.
2. Create `resume-tailor/sessions/<session>/source_resume.md`.
3. Treat `source_resume.md` as the source of truth.
4. Ask whether the user wants standard formatting or tailoring to a job description.
5. If tailoring, ingest the job post from a URL or pasted text and save it as `job_posting.md`.
6. Extract job requirements.
7. Revise the resume only using evidence in the source resume or explicit user additions.
8. Create `gap_analysis.md` for missing or weak evidence.
9. Create `claim_verification.md` mapping each revised claim to source evidence.
10. Remove unsupported claims before final delivery.

Read `references/resume_format.md` before editing resume content.
```

