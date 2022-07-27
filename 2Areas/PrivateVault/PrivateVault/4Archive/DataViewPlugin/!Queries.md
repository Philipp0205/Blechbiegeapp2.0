### Daily notes 
```dataview
TABLE type FROM #daily 
WHERE type > ""
```

### Active Projects
```dataview
TABLE status from #index
WHERE status = "active"
```

### Archived Projects
```dataview
TABLE status from #index
WHERE status = "archived"
```