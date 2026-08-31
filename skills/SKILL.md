---
name: stat432-fall2026-student
description: Set up the required GitHub folders or check and submit discussion questions, homework reports, and final-project files. Use this skill only when the student asks to set up those folders, check the technical format of one of these files, or submit it; do not use it to review substantive content.
metadata:
  version: "1.0.0"
---

# Student Repository Rules

Inspect content only as needed for mechanical format checks such as frontmatter, word count, markup balance, file type, self-containment, and page count. Do not evaluate, revise, summarize, or judge the substantive question, answers, analysis, or report.

`NN` always means a two-digit week number. Work only in the intended repository. Preserve unrelated files and Git history. Never expose credentials, rewrite history, or force-push.

## Repository Structure

```text
repository-root/
|-- .gitignore
|-- discussion/
|   `-- week-NN-question.md
|-- homework/
|   `-- week-NN/
|       `-- homework-NN.pdf or homework-NN.html
`-- project/
    |-- final-report.pdf or final-report.html
    `-- appendix.pdf or appendix.html
```

The local Git root, remote repository, current branch, and upstream branch must identify the same intended project. Working files may remain in `homework/week-NN/`; only the numbered PDF or HTML report is the homework submission.

## `.gitignore`

Use this root `.gitignore` during setup:

```gitignore
# Ignore everything at the repository root.
/*

# Keep the submission structure.
!/.gitignore
!/discussion/
!/homework/
!/project/

# Keep only weekly discussion questions.
/discussion/*
!/discussion/week-[0-9][0-9]-question.md

# Keep only final weekly homework reports.
/homework/*
!/homework/week-[0-9][0-9]/
/homework/week-[0-9][0-9]/*
!/homework/week-[0-9][0-9]/homework-[0-9][0-9].pdf
!/homework/week-[0-9][0-9]/homework-[0-9][0-9].html

# Keep only final-project files.
/project/*
!/project/final-report.pdf
!/project/final-report.html
!/project/appendix.pdf
!/project/appendix.html
```

The week number in a homework folder and report must still match; `.gitignore` cannot enforce that equality.

## Discussion Question

Use `discussion/week-NN-question.md` with exactly one YAML frontmatter block:

```markdown
---
id: wNN-student-id-short-topic
title: "Question title"
author: "Full Name (student-id)"
---

Question body.
```

A valid file has:

- the same two-digit `NN` in the filename and `id`;
- required `id`, `title`, and `author`, with a stable `id` using only letters, numbers, hyphens, and underscores;
- a title of at most 50 characters and a prose body of at most 200 words, excluding fenced code and mathematics;
- one nonempty Markdown body after the frontmatter;
- LaTeX uses `$...$` or `$$...$$`, with balanced delimiters and braces and no custom or unsafe commands;
- code blocks use closed triple-backtick fences labeled `r` or `python`;
- no content before the frontmatter, additional frontmatter, standalone `---` line, images, external links, raw HTML, or JavaScript; and
- the Markdown file is saved as UTF-8 and ends with a newline after the final line.

## Homework Submission

Use `homework/week-NN/homework-NN.pdf` or one self-contained `homework-NN.html`. The folder and report must use the same `NN`, and the file must open successfully. The QMD source, solutions, data, and figures are working materials, not required submission files.

## Final Project

Use `project/final-report.pdf` or one self-contained `final-report.html`, limited to 20 pages. An appendix may be `project/appendix.pdf` or one self-contained `appendix.html`; for HTML, use browser print preview to check the report length.

## Format and Submission Check

- Report only mechanical format results; leave substantive review to the student.
- The tracked path list matches the `.gitignore` allowlist; report extra tracked paths without reading or deleting them.
- A fresh fetch confirms that the local branch is not behind or diverged from its upstream.
- The staged file list contains only the intended submission files. Never use `git add .` or `git add -A` for a submission.
- An existing submission may be replaced in its required location. Check the replacement's format and stage only the intended file. When changing between PDF and HTML, remove the previous version only with student approval.
- `.gitignore` is committed during repository setup.
- Commit and push require student approval. The remote branch must show the expected files and commit afterward.
