---
title: "Naming Convention（命名规范）"
type: system
status: active
created: 2026-06-09
---

# Naming Convention（命名规范）

## Core Rule

Use stable English paths for the filesystem, and use bilingual display text for human-facing learning context.

## Folders

- Top-level folders use English Title Case: `Areas`, `Concepts`, `Sources`, `Assets`.
- Domain folders use stable English names: `Computer Science`, `Mathematics`, `Communications`.
- Keep structural folders separate from content folders. Images stay under `Assets/Images/...`; concepts stay under `Concepts/...`.

## Notes

- Concept notes that benefit from graph readability can use `English Term (中文 Term).md` or `English Term（中文术语）.md`.
- If a title is too long, keep the filename English and put Chinese in frontmatter aliases.
- Use frontmatter to preserve bilingual search:

```yaml
title: "Wireless Channel（无线信道）"
aliases:
  - 无线信道
  - Wireless Channel
```

## Images

- Images use lowercase English kebab-case.
- Keep image names semantic and short: `rayleigh-fading-amplitude-pdf.png`, not timestamp-only export names.
- Do not use spaces, timestamps, hash-only names, double punctuation, or typo-bearing names.
- Prefer this shape: `<topic>-<specific-object>.png`.
- If the source image is missing and the file is only a placeholder, include `missing` and `placeholder` in the filename.

## Captions And Understanding

- Do not make image filenames bilingual. Images do not appear as graph nodes, and English filenames are more stable for GitHub, URLs, and cross-platform sync.
- Put the Chinese explanation in the note text near the image, or in a dedicated concept note.
- When a term matters for English learning, write it as `English（中文）` the first time it appears.

## Rename Workflow

1. Rename the asset file.
2. Update every Obsidian embed that references it.
3. Run a broken-link scan before committing.
4. Do not delete unreferenced assets without a separate cleanup pass.
