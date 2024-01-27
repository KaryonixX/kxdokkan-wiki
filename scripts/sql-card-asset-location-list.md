---
Title: '[SQL] Card Asset Location List'
Sort: 1
---
```sql
SELECT
	cards.id AS "Card ID",
	cards.name AS "Card Name",
	card_sa_scripts.sa_scripts AS "SA Script LUA Files",
	'assets/ingame/battle/effect/' || passive_transformation_effect_pack.pack_name || '.cpk' AS "Passive Transformation CPK File",
	'assets/ingame/battle/effect/' || active_transformation_effect_pack.pack_name || '.cpk' AS "Active Transformation CPK File"
FROM
	cards
LEFT JOIN
	(
		SELECT
			card_specials.card_id,
			REPLACE(GROUP_CONCAT(DISTINCT (card_specials.eball_num_start || 'ki: assets/lua/ab_script/attack_sp/' || special_views.script_name || ".lua")), ',', x'0a') AS "sa_scripts"
		FROM
			card_specials
		LEFT JOIN
			special_views ON (special_views.id = card_specials.view_id)
		GROUP BY
			card_specials.card_id
	) "card_sa_scripts" ON (card_sa_scripts.card_id = cards.id)
LEFT JOIN 
	passive_skill_set_relations ON (passive_skill_set_relations.passive_skill_set_id = cards.passive_skill_set_id)
LEFT JOIN 
	passive_skills ON (passive_skills.id = passive_skill_set_relations.passive_skill_id)
LEFT JOIN 
	card_active_skills ON (card_active_skills.card_id = cards.id)
LEFT JOIN
	active_skills ON (active_skills.active_skill_set_id = card_active_skills.active_skill_set_id)
LEFT JOIN
	transformation_descriptions "passive_transformation" ON (passive_transformation.skill_id = passive_skills.id AND passive_transformation.skill_type = 'PassiveSkill')
LEFT JOIN
	transformation_descriptions "active_transformation" ON (active_transformation.skill_id = active_skills.id AND active_transformation.skill_type = 'ActiveSkill')
LEFT JOIN 
	passive_skills "transformation_passive_skill" ON (transformation_passive_skill.id = passive_transformation.skill_id)
LEFT JOIN 
	active_skills "transformation_active_skill" ON (transformation_active_skill.id = active_transformation.skill_id)
LEFT JOIN
	battle_params "passive_transformation_battle_params" ON (passive_transformation_battle_params.param_no = transformation_passive_skill.eff_value3 AND passive_transformation_battle_params.idx = 1)
LEFT JOIN
	effect_packs "passive_transformation_effect_pack" ON (passive_transformation_effect_pack.id = passive_transformation_battle_params.value)
LEFT JOIN
	effect_packs "active_transformation_effect_pack" ON (active_transformation_effect_pack.id = transformation_active_skill.thumb_effect_id)
WHERE
	cards.awaked_card_id IS NULL
```