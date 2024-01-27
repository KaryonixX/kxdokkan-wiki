---
Title: '[SQL] Causality Type Search'
---
Searches all skill tables for usage of a particular `causality_type`. Will return what table, the `id`, the description, and the causality value parameters.

Replace the `00000` in the first line of the script with the `causality_type` id.

```sql
WITH VARIABLES AS (SELECT 00000 AS "causality_type")
SELECT
	'active_skill_sets' AS "type",
	active_skill_sets.id,
	active_skill_sets.condition_description,
	skill_causalities.causality_type AS "causality_type",
	skill_causalities.cau_val1,
	skill_causalities.cau_val2,
	skill_causalities.cau_val3
FROM
	active_skill_sets, json_each(active_skill_sets.causality_conditions, '$.compiled')
LEFT JOIN
	skill_causalities ON (skill_causalities.id = json_each.value)
WHERE
	json_each.value IN (
		SELECT
			skill_causalities.id
		FROM
			skill_causalities, VARIABLES
		WHERE
			skill_causalities.causality_type = VARIABLES.causality_type
	)
UNION
SELECT
	'passive_skills' AS "type",
	passive_skills.id,
	passive_skills.description,
	skill_causalities.causality_type AS "causality_type",
	skill_causalities.cau_val1,
	skill_causalities.cau_val2,
	skill_causalities.cau_val3
FROM
	passive_skills, json_each(passive_skills.causality_conditions, '$.compiled')
LEFT JOIN
	skill_causalities ON (skill_causalities.id = json_each.value)
WHERE
	json_each.value IN (
		SELECT
			skill_causalities.id
		FROM
			skill_causalities, VARIABLES
		WHERE
			skill_causalities.causality_type = VARIABLES.causality_type
	)
UNION
SELECT
	'leader_skills' AS "type",
	leader_skills.id,
	leader_skills.description,
	skill_causalities.causality_type AS "causality_type",
	skill_causalities.cau_val1,
	skill_causalities.cau_val2,
	skill_causalities.cau_val3
FROM
	leader_skills, json_each(leader_skills.causality_conditions, '$.compiled')
LEFT JOIN
	skill_causalities ON (skill_causalities.id = json_each.value)
WHERE
	json_each.value IN (
		SELECT
			skill_causalities.id
		FROM
			skill_causalities, VARIABLES
		WHERE
			skill_causalities.causality_type = VARIABLES.causality_type
	)
UNION
SELECT
	'enemy_skills' AS "type",
	enemy_skills.id,
	enemy_skills.description,
	skill_causalities.causality_type AS "causality_type",
	skill_causalities.cau_val1,
	skill_causalities.cau_val2,
	skill_causalities.cau_val3
FROM
	enemy_skills, json_each(enemy_skills.causality_conditions, '$.compiled')
LEFT JOIN
	skill_causalities ON (skill_causalities.id = json_each.value)
WHERE
	json_each.value IN (
		SELECT
			skill_causalities.id
		FROM
			skill_causalities, VARIABLES
		WHERE
			skill_causalities.causality_type = VARIABLES.causality_type
	)
UNION
SELECT
	'specials' AS "type",
	specials.id,
	special_sets.description,
	skill_causalities.causality_type AS "causality_type",
	skill_causalities.cau_val1,
	skill_causalities.cau_val2,
	skill_causalities.cau_val3
FROM
	specials, json_each(specials.causality_conditions, '$.compiled')
LEFT JOIN
	special_sets ON (special_sets.id = specials.special_set_id)
LEFT JOIN
	skill_causalities ON (skill_causalities.id = json_each.value)
WHERE
	json_each.value IN (
		SELECT
			skill_causalities.id
		FROM
			skill_causalities, VARIABLES
		WHERE
			skill_causalities.causality_type = VARIABLES.causality_type
	)
UNION
SELECT
	'potential_skills' AS "type",
	potential_skills.id,
	potential_skills.description,
	skill_causalities.causality_type AS "causality_type",
	skill_causalities.cau_val1,
	skill_causalities.cau_val2,
	skill_causalities.cau_val3
FROM
	potential_skills, json_each(potential_skills.causality_conditions, '$.compiled')
LEFT JOIN
	skill_causalities ON (skill_causalities.id = json_each.value)
WHERE
	json_each.value IN (
		SELECT
			skill_causalities.id
		FROM
			skill_causalities, VARIABLES
		WHERE
			skill_causalities.causality_type = VARIABLES.causality_type
	)
UNION
SELECT
	'special_bonuses' AS "type",
	special_bonuses.id,
	special_bonuses.description,
	skill_causalities.causality_type AS "causality_type",
	skill_causalities.cau_val1,
	skill_causalities.cau_val2,
	skill_causalities.cau_val3
FROM
	special_bonuses, json_each(special_bonuses.causality_conditions, '$.compiled')
LEFT JOIN
	skill_causalities ON (skill_causalities.id = json_each.value)
WHERE
	json_each.value IN (
		SELECT
			skill_causalities.id
		FROM
			skill_causalities, VARIABLES
		WHERE
			skill_causalities.causality_type = VARIABLES.causality_type
	)
```