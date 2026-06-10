---
title: "Home"
type: home
status: evergreen
visibility: public
---

# Home

## Study Areas

- [[Mathematics MOC]]
- [[Computer Science MOC]]
- [[Communications MOC]]

## Topic Maps

- [[Wireless Channel MOC]]
- [[Information Theory MOC]]
- [[Concepts MOC]]
- [[Study Map]]

## Current Public Notes

```dataview
TABLE area, subarea, status, file.mtime AS modified
FROM "Areas" OR "Concepts" OR "Maps"
WHERE !contains(file.path, "System")
SORT area ASC, subarea ASC, file.name ASC
```

## Recent

```dataview
LIST
FROM ""
WHERE !contains(file.path, ".obsidian") AND !contains(file.path, "System")
SORT file.mtime DESC
LIMIT 20
```
