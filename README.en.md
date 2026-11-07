# resume2JD | No More Resume Writing

[简体中文](README.md)

**Provide a job description and automatically get a matching, tailored resume.**

resume2JD is an AI Skill for job applications. Organize your experience into a career master—yes, the opposite of a condensed resume—then send an Agent a job description (JD) as a screenshot or text. It produces a tailored resume (HTML/PDF), fit analysis, role-specific interview simulations, and targeted candidate questions for that role, reducing repetitive resume editing. Every statement comes from real experience; nothing is invented.

## What you get

- **Tailored resume:** Markdown and a standalone HTML file; save as PDF through a browser, or use PDFKit automatically when the environment already supports it.
- **Fit analysis:** key requirements, supporting evidence, strengths, gaps, and an estimated screening-invitation range.
- **Interview simulation and candidate questions:** infer 1–3 interviewer roles and provide 8–12 role-specific questions, pressure follow-ups, an approximately 60-second self-introduction, an interview risk radar, and role-specific questions to ask. Answers retain links to real career evidence.
- **Traceability:** key resume claims link back to stable career-master IDs without inventing skills, responsibilities, metrics, or outcomes.

> The invitation range is an uncalibrated judgment based only on the resume and JD. It is not a measured pass rate or an employment guarantee.

## Why “No More Resume Writing”

In the AI era, role boundaries are changing, job definitions are becoming less clear-cut, and new or hybrid roles are becoming more common. A useful resume should not merely repeat JD keywords. It should answer two questions: **what problem does this role need to solve, and which real experiences prove that you can solve it?** Keep one growing career master and reorganize its evidence for each application.

## Requirements

- An AI Agent that can read and write local files; image understanding is required for JD screenshots.
- A modern browser: Microsoft Edge on Windows, Safari on macOS, or Firefox. **Chrome is not required.**
- No Node.js, Python, PDFKit, or API Key setup is needed for the normal workflow. The chosen AI product may have its own account or model requirements.

This is not a standalone application or hosted service. An Agent must read and follow `SKILL.md`.

## Quick start

### 1. Get and open the project

- Without Git: choose **Code → Download ZIP** on GitHub, extract it, and open the `resume2JD` folder in an Agent.
- With Git: run:

```bash
git clone https://github.com/Gzz9527/resume2JD.git
```

Skill-aware Agents may register this directory according to their product documentation. Workspace-based Agents can open the folder directly.

### 2. Create a career master with the Agent

Manual completion of the full template is not required. Source files remain unchanged.

**If you have an old resume, career notes, or text documents**

Place them in `inputs/`, then send:

```text
Read SKILL.md in this workspace.
I do not have a career master yet. Initialize one from the materials in inputs/.
Create a draft first and list missing or conflicting facts. Do not modify the sources or invent information.
```

You may also paste the old resume or career notes directly into the conversation.

**If you have no organized materials**

```text
Read SKILL.md in this workspace.
Help me create a career master through step-by-step questions, starting with basic information,
my most recent role, and one representative project.
```

**If you prefer manual editing**

Copy `templates/个人详历快速模板.md` to `个人详历.md` in the repository root. Start with basic information, work experience, representative projects, and education. Use `templates/个人详历模板.md` later when you want a fuller evidence library.

Initialization creates `个人详历.draft.md` by default and never overwrites an existing master. After reviewing it, send “Confirm this draft as my career master.” The Agent may then turn it into `个人详历.md` only if that file does not already exist. The confirmed master is read-only during resume generation.

### 3. Send a JD

Send a JD screenshot or paste its text, then say:

```text
Create a tailored resume from 个人详历.md and this JD.
```

The Agent selects and organizes real evidence instead of reformatting every experience. Each run uses a new directory and preserves earlier versions.

## PDF without extra setup

1. Open the generated HTML and click **“打印 / 保存 PDF”**, or use the browser's print command.
2. Choose **Save as PDF**.
3. Select **A4, portrait, 100%/default scale, default margins**, and disable browser headers and footers.

Use Edge on Windows or Safari on macOS; Chrome is unnecessary. This path creates a browser-printed PDF and must not be described as PDFKit output.

**PDFKit is an optional enhancement, not a prerequisite.** The Agent uses it only when generation and validation are already available. It must not ask a normal user to install a programming environment just to produce an application-ready PDF. If automatic generation is unavailable, it must say so and provide the HTML printing path above.

## Run the fictional demo

All people, companies, metrics, contact details, and vacancies in `examples/demo/` are fictional. Send:

```text
Read SKILL.md and run the full workflow with examples/demo/career-master.md and
examples/demo/job-description.md. Write the results to outputs/demo-run/.
```

Compare the results with `examples/demo/expected/`. Wording may vary by model; check factual fidelity, source mappings, file completeness, and HTML printing.

## Default outputs

Each run creates `outputs/<version>/` containing:

- `JD原文.md`: source JD text, with unreadable screenshot content marked for confirmation.
- `<name>-<target-role>-<target-company>.md`: editable resume and ATS-friendly source text.
- `<name>-<target-role>-<target-company>.html`: standalone visual and print-ready resume.
- `<name>-<target-role>-<target-company>.pdf`: generated automatically when supported, or saved manually from HTML.
- `岗位匹配与邀约评估.md`: fit analysis, source mappings, and invitation range.
- `面试模拟与反问.md`: interviewer-role inference, 8–12 role-specific questions, pressure follow-ups, opening preparation, risk radar, and targeted candidate questions.
- `校验与待确认.md`: created only when failures, suggestions, or uncertain facts need attention.

## Repository layout

```text
resume2JD/
├── SKILL.md
├── templates/
│   ├── 个人详历快速模板.md
│   ├── 个人详历模板.md
│   └── visual-template.html
├── examples/demo/
├── README.md
├── README.en.md
├── LICENSE
└── NOTICE
```

## Privacy and limitations

- Root career masters, drafts, `inputs/`, and `outputs/` are covered by `.gitignore`, but always inspect `git status` before committing.
- Never place real contact details, career masters, JDs, confidential employer data, or credentials in public examples, issues, pull requests, screenshots, or CI logs.
- Cloud AI products may send personal data to external providers. Review their data policies or choose an appropriate model deployment.
- The read-only rule is an Agent instruction, not filesystem enforcement. Back up important records.
- HTML makes no external font or script requests and works offline. Review all facts, pagination, and contact details before applying.

## License and contributions

Original project content is available under the [MIT License](LICENSE). The visual template is derived from a personally designed resume webpage; see [NOTICE](NOTICE) for provenance and sanitization details.

Contributions to career-master structure, factual validation, role matching, Chinese typography, and cross-platform workflows are welcome. Use only fictional or sanitized data in contributions.
