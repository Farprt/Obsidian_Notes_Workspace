---
title: "Dashboard"
type: home
status: evergreen
---
# Dashboard

## By Type
```dataview
TABLE length(rows) AS count
FROM ""
WHERE type
GROUP BY type
SORT type ASC
```

## To Review
```dataview
TABLE area, subarea, file.mtime AS modified
FROM ""
WHERE status = "to-review"
SORT file.mtime DESC
```
