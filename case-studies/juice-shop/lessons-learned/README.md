## Lesson — AI-generated content still needs QA review

**Context:** TASK-001 - Review documentation (US-001 - Understand
the Business Domain)

**What happened:**
While drafting `documentation-review.md` with AI assistance
(Claude), a stray non-English character ("未") was introduced into
the "Information That Remains a Hypothesis" section. It was caught
during manual review before the document was committed.

**Why it matters:**
This is a concrete example of why AI-assisted documentation cannot
be treated as final output. As a Quality Engineer, reviewing
AI-generated artifacts with the same rigor as human-written ones is
part of the job — not an optional step.

**Action taken:**
The document was reviewed line by line before being marked final;
the error was corrected prior to commit.

**Takeaway for future tasks:**
Every AI-assisted deliverable in this lab will go through a manual
QA pass before being committed, regardless of how polished it looks
at first glance.
