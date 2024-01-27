---
Title: Future Proofing Your SQL
Description: Create future proof and non-clashing patches.
---
The main reason patches become outdated or crash is due to the reuse of a database table id.

This guide will show you how you can make sure you're always automatically using unique ids.

```sql
CREATE TEMPORARY TABLE NEW_ID (id INT);

INSERT INTO
    equipment_skill_items (name, description, grade, selling_exchange_point, hp, attack, defense, equipment_skill_limitation_set_id, icon_image_id, created_at, updated_at)
VALUES
    ("Crit and AA", "Gives crit and aa", "gold", 1, 5000, 5000, 5000, NULL, 55, strftime('%Y-%m-%d %H-%M-%S', 'now'), strftime('%Y-%m-%d %H-%M-%S', 'now'));
    
INSERT INTO NEW_ID SELECT last_insert_rowid();

INSERT INTO
    equipment_skills (equipment_skill_item_id, potential_skill_id, status_type, level, created_at, updated_at)
VALUES
    ((SELECT id FROM NEW_ID), 1, NULL, 20, strftime('%Y-%m-%d %H-%M-%S', 'now'), strftime('%Y-%m-%d %H-%M-%S', 'now')),
    ((SELECT id FROM NEW_ID), 2, NULL, 20, strftime('%Y-%m-%d %H-%M-%S', 'now'), strftime('%Y-%m-%d %H-%M-%S', 'now'));
    
DROP TEMPORARY TABLE NEW_ID;
```

**Actual guide coming soon...**