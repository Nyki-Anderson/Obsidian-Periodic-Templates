### Notes Modified

```dataview
TABLE WITHOUT ID link(file.link, aliases[0]) as "File", scope as "Scope", type as "Type", description as "Description"
WHERE file.mtime >= date(2024-01-03) - dur(1 day) 
	AND file.path != this.file.path
	AND file.ctime != date(2024-01-03)
SORT file.mtime DESC
```

### Notes Created

```dataview
TABLE WITHOUT ID link(file.link, aliases[0]) as "File", scope as "Scope", type as "Type", description as "Description"
WHERE file.ctime >= date(2024-01-03) - dur(1 day) 
	AND file.path != this.file.path
SORT file.ctime DESC
```