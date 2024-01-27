---
Title: '[Python] Database Search'
---
**Example:**
Find all instances of Namek Goku (ID: `1017181`) - `python db_search.py 1017181`

```python
import sqlite3
import json
import sys

filename = "database.db"
search_term = sys.argv[1]
locs = []

with sqlite3.connect(filename) as conn:
    conn.row_factory = sqlite3.Row
    cursor = conn.cursor()
    cursor.execute("SELECT name FROM sqlite_master WHERE type='table'")
    for tablerow in cursor.fetchall():
        table = tablerow[0]
        cursor.execute(f"SELECT * FROM {table}")
        for row in cursor:
            for field in row.keys():
                if str(row[field]) == search_term:
                    locs.append({
                        "table": table,
                        "row_id": row["id"],
                        "column": field,
                    })

print(json.dumps(locs, indent="\t"))
```