---
name: github-readme
description: >
  Creates and improves GitHub README files with badges, description, Mermaid diagrams, preview images, objective, quick start, and examples. Use when the user wants to create a README, write a GitHub README, document a repo, add badges to README, or improve an existing README. Always asks questions first (build mode) before writing.
---

# GitHub README Skill

Creates and improves GitHub repository READMEs with a professional structure: badges, description, Mermaid diagrams, preview (image/GIF), objective, quick start and examples. **Build mode:** the agent asks before writing and reminds the user they can change everything.

---

## Required rule: ask before writing

**Never** generate the full README immediately. Operate in **build mode**:

1. **Before writing**, ask questions to gather:
   - Project/repository name
   - Main languages, frameworks and libs (for badges)
   - Short description (one or two sentences)
   - Main project objective
   - Quick start steps (commands, prerequisites)
   - Whether a Mermaid diagram is needed (flow, architecture, pipeline)
   - Whether they want an image or GIF preview of the application
   - Extra sections (commands, project structure, API, tests, license)

2. **Summarise** the answers and ask: *"Do you want to change anything before I generate the README?"*

3. **Only after** confirmation (or the user saying to proceed), generate the README content.

4. **At the end**, say the README is a draft and can be edited as needed.

If the user has already provided all the information in a message, still list what will be used and ask *"Do you confirm or want to change anything?"* before generating.

---

## README structure

Follow this order and include only what makes sense for the project. See [reference.md](reference.md) for examples and details.

| Section | Content |
|--------|----------|
| **Title** | Project/repo name (H1), optionally with emoji (e.g. `# 🚀 Project Name`). |
| **Version / tagline** | Optional line with version or short phrase in **bold**. |
| **Badges** | Icons for languages, libs and tools (shields.io). Single line of badges, no breaks. |
| **Description** | One or two paragraphs: what the project is, who it is for, main highlight. |
| **Preview** | If applicable: image or GIF of the application with caption. |
| **How it works / Objective** | Flow, pipeline or objective; optionally with Mermaid diagram or exported image. |
| **Quick start** | Prerequisites and numbered steps (clone, install, config, run). With code blocks when appropriate. |
| **Commands / Table** | Table of useful commands (e.g. `npm run X`, `rails Y`) if relevant. |
| **Project structure** | Table or tree of main folders and what they do. |
| **Examples** | Minimal usage example (commands or code). |
| **Limitations / Recommendations** | Optional; only if it makes sense. |
| **License** | License (e.g. MIT) and link to LICENSE file. |

---

## Badges (shields.io)

- Use **one line** of badges, no breaks, for language, runtime, main frameworks and libs.
- Typical format: `[![Name](shield-URL)](optional-link)`
- Example text: Node.js 18+, Rails 8, PostgreSQL, Docker, Mermaid, License MIT.
- Colours and style: keep consistent (for-the-badge or flat; see [reference.md](reference.md)).

---

## Mermaid and images

- **Mermaid:** If the user wants a diagram (flow, pipeline, architecture), propose the Mermaid code and note that GitHub renders Mermaid natively; for .docx or other contexts, you may need to export PNG (e.g. `mermaid-cli`) and reference the image in the README.
- **Preview:** If there is an image or GIF preview, place it after the description, with caption in *italics*.

---

## Tone and style

- Clear, objective language.
- Lists and tables for commands and structure.
- Code blocks with syntax highlighting (bash, javascript, etc.).
- Keep the README navigable: optional TOC for large projects.

---

## After generating

- Tell the user they can **change** any part.
- If something is missing (e.g. env vars, tests), suggest it can be added in a next iteration.

---

## References

- Detailed structure and block examples: [reference.md](reference.md).
