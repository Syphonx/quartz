---
publish: true
---

```dataview
TABLE WITHOUT ID (tag + "(" + length(rows.file.link) + ")") AS Tags
FROM "Published"
WHERE file.tags 
FLATTEN file.tags AS tag 
GROUP BY tag
SORT length(rows.file.link) DESC
```
