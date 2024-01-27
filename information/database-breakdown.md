---
title: Database Breakdown
nav_order: 2
---
---
[**Thanks to T6 for allowing me to reuse the UD wiki!**](https://twitter.com/ThievingSix) 

[**Be sure to check out his new Dokkan Wiki**](https://dokkan.wiki/)
## act_cure_schedules

Description of `act_cure_schedules` table.

**Columns:**

* `id`
    * Type: `number, required`
* `seconds_per_cure_one_act`
    * Type: `number, required`
* `start_at`
    * Type: `date/time, required`
* `end_at`
    * Type: `date/time, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## act_items

Description of `act_items` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `description`
    * Type: `text, required`
* `rarity`
    * Type: `number, required`
* `recover_value`
    * Type: `number, required`
* `selling_exchange_point`
    * Type: `number, required`
* `created_at`
    * Type: `date/time, required`
* `updated_at`
    * Type: `date/time, required`

  
  


## areas

Description of `areas` table.

**Columns:**

* `id`
    * Type: `number, required`
* `type`
    * Type: `text`
* `category`
    * Type: `number`
* `world_id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `prev_area_id`
    * Type: `number`
* `all_clear_bonus_stones`
    * Type: `number`
* `bgm_id`
    * Type: `number`
* `area_icon_id`
    * Type: `number`
* `width`
    * Type: `number`
* `height`
    * Type: `number`
* `split`
    * Type: `number`
* `layer0`
    * Type: `text`
* `layer1`
    * Type: `text`
* `layer2`
    * Type: `text`
* `layer3`
    * Type: `text`
* `event_image_path`
    * Type: `text`
* `banner_image_path`
    * Type: `text`
* `minibanner_image_path`
    * Type: `text`
* `listbutton_image_path`
    * Type: `text`
* `is_listbutton_visible`
    * Type: `boolean, required`
* `event_priority`
    * Type: `number, required`
* `announcement_id`
    * Type: `number`
* `is_quest_num_visible`
    * Type: `boolean, required`
* `first_released_at`
    * Type: `date/time`
* `locked_by`
    * Type: `text`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## active_skill_sets

Description of `active_skill_sets` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `effect_description`
    * Type: `text, required`
* `condition_description`
    * Type: `text, required`
* `turn`
    * Type: `number, required`
* `exec_limit`
    * Type: `number, required`
* `causality_conditions`
    * Type: `text`
* `ultimate_special_id`
    * Type: `number`
* `special_view_id`
    * Type: `number`
* `bgm_id`
    * Type: `number`
* `created_at`
    * Type: `date/time, required`
* `updated_at`
    * Type: `date/time, required`

  
  


## active_skills

Description of `active_skills` table.

**Columns:**

* `id`
    * Type: `number, required`
* `active_skill_set_id`
    * Type: `number, required`
    * Links to [active_skill_sets](#active_skill_sets)
* `target_type`
    * Type: `number, required`
    * `1`: Target self
    * `2`: Target allies
* `sub_target_type_set_id`
    * Type: `number`
* `calc_option`
    * Type: `number, required`
    * [List of Calc Options](/wiki/information/database-function-tables#calc-options)
* `efficacy_type`
    * Type: `number, required`
    * [List of Efficacy Types](/wiki/information/database-function-tables#efficacy-types)
* `eff_val1`
    * Type: `number, required`
* `eff_val2`
    * Type: `number, required`
* `eff_val3`
    * Type: `number, required`
* `thumb_effect_id`
    * Type: `number`
    * Links to [effect_packs](#effect_packs)
* `effect_se_id`
    * Type: `number`
* `created_at`
    * Type: `date/time, required`
* `updated_at`
    * Type: `date/time, required`

  
  


## area_conditions

Description of `area_conditions` table.

**Columns:**

* `id`
    * Type: `number, required`
* `area_id`
    * Type: `number, required`
* `type`
    * Type: `text, required`
* `conditions`
    * Type: `text`
* `comment`
    * Type: `text, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## area_icons

Description of `area_icons` table.

**Columns:**

* `id`
    * Type: `number, required`
* `world_id`
    * Type: `number, required`
* `image`
    * Type: `text`
* `icon_x`
    * Type: `number`
* `icon_y`
    * Type: `number`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## area_tabs

Description of `area_tabs` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text`
* `area_category_ids`
    * Type: `text`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## awakening_items

Description of `awakening_items` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `description`
    * Type: `text, required`
* `zeni`
    * Type: `number, required`
* `rarity`
    * Type: `number, required`
* `selling_exchange_point`
    * Type: `number, required`
* `event_jumpable`
    * Type: `boolean`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## battle_params

Description of `battle_params` table.

**Columns:**

* `id`
    * Type: `number, required`
* `param_no`
    * Type: `number, required`
* `idx`
    * Type: `number, required`
* `value`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## beginners_guides

Description of `beginners_guides` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `start_image`
    * Type: `text, required`
* `start_at`
    * Type: `date/time, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## bgm_schedules

Description of `bgm_schedules` table.

**Columns:**

* `id`
    * Type: `number, required`
* `bgm_id`
    * Type: `number, required`
* `scene_name`
    * Type: `text, required`
* `start_at`
    * Type: `date/time, required`
* `end_at`
    * Type: `date/time, required`
* `created_at`
    * Type: `date/time, required`
* `updated_at`
    * Type: `date/time, required`

  
  


## boost_schedules

Description of `boost_schedules` table.

**Columns:**

* `id`
    * Type: `number, required`
* `max_point`
    * Type: `number, required`
* `seconds_per_cure_one_point`
    * Type: `number, required`
* `start_at`
    * Type: `date/time, required`
* `end_at`
    * Type: `date/time, required`
* `created_at`
    * Type: `date/time, required`
* `updated_at`
    * Type: `date/time, required`

  
  


## budokais

Description of `budokais` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `description`
    * Type: `text, required`
* `start_at`
    * Type: `date/time, required`
* `end_at`
    * Type: `date/time, required`
* `collecting_end_at`
    * Type: `date/time, required`
* `result_end_at`
    * Type: `date/time, required`
* `mission_reward_image_path`
    * Type: `text, required`
* `banner_image_path`
    * Type: `text, required`
* `listbutton_image_path`
    * Type: `text`
* `entry_script_id`
    * Type: `number, required`
* `description_script_id`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## budokai_box_rankings

Description of `budokai_box_rankings` table.

**Columns:**

* `id`
    * Type: `number, required`
* `budokai_id`
    * Type: `number, required`
* `prev_budokai_id`
    * Type: `number`
* `prev_budokai_box_ranking_id`
    * Type: `number`
* `player_max_count`
    * Type: `number, required`
* `box_max_count`
    * Type: `number`
* `start_at`
    * Type: `date/time, required`
* `end_at`
    * Type: `date/time, required`
* `collecting_end_at`
    * Type: `date/time, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## budokai_box_ranking_rewards

Description of `budokai_box_ranking_rewards` table.

**Columns:**

* `id`
    * Type: `number, required`
* `budokai_box_ranking_reward_range_id`
    * Type: `number, required`
* `item_id`
    * Type: `number, required`
* `item_type`
    * Type: `text, required`
* `quantity`
    * Type: `number, required`
* `card_exp_init`
    * Type: `number, required`
* `description`
    * Type: `text, required`
* `gift_description`
    * Type: `text, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## budokai_box_ranking_reward_ranges

Description of `budokai_box_ranking_reward_ranges` table.

**Columns:**

* `id`
    * Type: `number, required`
* `budokai_box_ranking_id`
    * Type: `number, required`
* `start_value`
    * Type: `number, required`
* `end_value`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## budokai_helps

Description of `budokai_helps` table.

**Columns:**

* `id`
    * Type: `number, required`
* `budokai_help_category_id`
    * Type: `number, required`
* `num`
    * Type: `number`
* `title`
    * Type: `text, required`
* `description`
    * Type: `text`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## budokai_help_bodies

Description of `budokai_help_bodies` table.

**Columns:**

* `id`
    * Type: `number, required`
* `budokai_help_id`
    * Type: `number`
* `image_path`
    * Type: `text`
* `description`
    * Type: `text`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## budokai_help_categories

Description of `budokai_help_categories` table.

**Columns:**

* `id`
    * Type: `number, required`
* `num`
    * Type: `number`
* `title`
    * Type: `text, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## budokai_leagues

Description of `budokai_leagues` table.

**Columns:**

* `id`
    * Type: `number, required`
* `budokai_id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `league`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## budokai_missions

Description of `budokai_missions` table.

**Columns:**

* `id`
    * Type: `number, required`
* `budokai_id`
    * Type: `number, required`
* `mission_type`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `priority`
    * Type: `number, required`
* `target_value`
    * Type: `number, required`
* `prev_budokai_mission_id`
    * Type: `number`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## budokai_mission_rewards

Description of `budokai_mission_rewards` table.

**Columns:**

* `id`
    * Type: `number, required`
* `budokai_mission_id`
    * Type: `number, required`
* `item_id`
    * Type: `number, required`
* `item_type`
    * Type: `text, required`
* `quantity`
    * Type: `number, required`
* `card_exp_init`
    * Type: `number, required`
* `description`
    * Type: `text, required`
* `gift_description`
    * Type: `text, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## budokai_motivations

Description of `budokai_motivations` table.

**Columns:**

* `id`
    * Type: `number, required`
* `budokai_id`
    * Type: `number, required`
* `priority`
    * Type: `number, required`
* `player_description`
    * Type: `text, required`
* `announcer_description`
    * Type: `text`
* `additional_hp_percent`
    * Type: `number, required`
* `max_hp_percent`
    * Type: `number, required`
* `additional_atk_percent`
    * Type: `number, required`
* `max_atk_percent`
    * Type: `number, required`
* `additional_def_percent`
    * Type: `number, required`
* `max_def_percent`
    * Type: `number, required`
* `additional_point_percent`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## budokai_motivation_unlock_conditions

Description of `budokai_motivation_unlock_conditions` table.

**Columns:**

* `id`
    * Type: `number, required`
* `budokai_motivation_id`
    * Type: `number, required`
* `type`
    * Type: `text`
* `description`
    * Type: `text`
* `conditions`
    * Type: `text`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## budokai_ranks

Description of `budokai_ranks` table.

**Columns:**

* `id`
    * Type: `number, required`
* `budokai_id`
    * Type: `number, required`
* `budokai_league_id`
    * Type: `number, required`
* `rank`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `point`
    * Type: `number, required`
* `bonus`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## budokai_ranking_gifts

Description of `budokai_ranking_gifts` table.

**Columns:**

* `id`
    * Type: `number, required`
* `budokai_ranking_gift_set_id`
    * Type: `number, required`
* `description`
    * Type: `text`
* `item_type`
    * Type: `text, required`
* `item_id`
    * Type: `number, required`
* `quantity`
    * Type: `number, required`
* `card_exp_init`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## budokai_ranking_gift_sets

Description of `budokai_ranking_gift_sets` table.

**Columns:**

* `id`
    * Type: `number, required`
* `budokai_id`
    * Type: `number, required`
* `order`
    * Type: `number, required`
* `ranking`
    * Type: `text, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## budokai_opponent_attack_weights

Description of `budokai_opponent_attack_weights` table.

**Columns:**

* `id`
    * Type: `number, required`
* `budokai_id`
    * Type: `number, required`
* `round`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## budokai_opponent_attack_weight_lines

Description of `budokai_opponent_attack_weight_lines` table.

**Columns:**

* `id`
    * Type: `number, required`
* `budokai_opponent_attack_weight_id`
    * Type: `number, required`
* `ball_count`
    * Type: `number, required`
* `rate`
    * Type: `number, required`

  
  


## budokai_progress_selifs

Description of `budokai_progress_selifs` table.

**Columns:**

* `id`
    * Type: `number, required`
* `budokai_id`
    * Type: `number, required`
* `round`
    * Type: `number, required`
* `image_path`
    * Type: `text`
* `description`
    * Type: `text`

  
  


## card_active_skills

Description of `card_active_skills` table.

**Columns:**

* `id`
    * Type: `number, required`
* `card_id`
    * Type: `number, required`
* `active_skill_set_id`
    * Type: `number, required`
* `created_at`
    * Type: `date/time, required`
* `updated_at`
    * Type: `date/time, required`

  
  


## card_awakening_routes

Description of `card_awakening_routes` table.

**Columns:**

* `id`
    * Type: `number, required`
* `type`
    * Type: `text, required`
* `card_id`
    * Type: `number, required`
* `awaked_card_id`
    * Type: `number`
* `num`
    * Type: `number`
* `card_awakening_set_id`
    * Type: `number, required`
* `optimal_awakening_step`
    * Type: `number`
* `description`
    * Type: `text`
* `priority`
    * Type: `number`
* `open_at`
    * Type: `date/time`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## card_awakening_sets

Description of `card_awakening_sets` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text`
* `description`
    * Type: `text`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## card_awakenings

Description of `card_awakenings` table.

**Columns:**

* `id`
    * Type: `number, required`
* `num`
    * Type: `number, required`
* `awakening_item_id`
    * Type: `number, required`
* `quantity`
    * Type: `number, required`
* `card_awakening_set_id`
    * Type: `number`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## card_card_categories

Description of `card_card_categories` table.

**Columns:**

* `id`
    * Type: `number, required`
* `card_id`
    * Type: `number, required`
* `card_category_id`
    * Type: `number, required`
* `num`
    * Type: `number, required`
* `created_at`
    * Type: `date/time, required`
* `updated_at`
    * Type: `date/time, required`

  
  


## card_categories

Description of `card_categories` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `priority`
    * Type: `number, required`
* `open_at`
    * Type: `date/time, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## card_exps

Description of `card_exps` table.

**Columns:**

* `id`
    * Type: `number, required`
* `lv`
    * Type: `number, required`
* `exp_type`
    * Type: `number, required`
* `exp_total`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## card_growths

Description of `card_growths` table.

**Columns:**

* `id`
    * Type: `number, required`
* `grow_type`
    * Type: `number, required`
* `lv`
    * Type: `number, required`
* `coef`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## card_unique_infos

Description of `card_unique_infos` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `kana`
    * Type: `text`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## card_motions

Description of `card_motions` table.

**Columns:**

* `id`
    * Type: `number, required`
* `card_id`
    * Type: `number, required`
* `category`
    * Type: `number, required`
* `filename`
    * Type: `text`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## card_specials

Description of `card_specials` table.

**Columns:**

* `id`
    * Type: `number, required`
* `card_id`
    * Type: `number, required`
* `special_set_id`
    * Type: `number, required`
* `lv_start`
    * Type: `number, required`
* `eball_num_start`
    * Type: `number, required`
* `view_id`
    * Type: `number, required`
* `special_bonus_id1`
    * Type: `number, required`
* `special_bonus_lv1`
    * Type: `number, required`
* `bonus_view_id1`
    * Type: `number, required`
* `special_bonus_id2`
    * Type: `number, required`
* `special_bonus_lv2`
    * Type: `number, required`
* `bonus_view_id2`
    * Type: `number, required`
* `is_ultra_special`
    * Type: `boolean, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## card_training_skill_lvs

Description of `card_training_skill_lvs` table.

**Columns:**

* `id`
    * Type: `number, required`
* `card_id`
    * Type: `number, required`
* `skill_lv`
    * Type: `number, required`
* `condition`
    * Type: `number, required`
* `probability`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## card_training_skill_lv_up_probs

Description of `card_training_skill_lv_up_probs` table.

**Columns:**

* `id`
    * Type: `number, required`
* `rarity`
    * Type: `text, required`
* `n`
    * Type: `number, required`
* `r`
    * Type: `number, required`
* `sr`
    * Type: `number, required`
* `ssr`
    * Type: `number, required`
* `ur`
    * Type: `number, required`
* `lr`
    * Type: `number, required`

  
  


## card_training_field_exp_up_probs

Description of `card_training_field_exp_up_probs` table.

**Columns:**

* `id`
    * Type: `number, required`
* `key`
    * Type: `text, required`
* `effect`
    * Type: `number, required`
* `success_prob_percent`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## cards

Description of `cards` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
    * Display name of card
* `character_id`
    * Type: `number, required`
    * Links to [characters](#characters)
* `awaked_card_id`
    * Type: `number`
    * Links to [cards](#cards)
    * Linked card is the Z-Awakened version of the base card
* `card_unique_info_id`
    * Type: `number, required`
    * Links to [card_unique_infos](#card_unique_infos)
* `cost`
    * Type: `number, required`
    * Team cost
* `rarity`
    * Type: `number, required`
    * `0`: N
    * `1`: R
    * `2`: SR
    * `3`: SSR
    * `4`: UR
    * `5`: LR
* `hp_init`
    * Type: `number, required`
    * HP at level 1
* `hp_max`
    * Type: `number, required`
    * HP at max level
* `atk_init`
    * Type: `number, required`
    * Attack at level 1
* `atk_max`
    * Type: `number, required`
    * Attack at max level
* `def_init`
    * Type: `number, required`
    * Defense at level 1
* `def_max`
    * Type: `number, required`
    * Defense at max level
* `element`
    * Type: `number, required`
    * `0`: AGL
    * `1`: TEQ
    * `2`: INT
    * `3`: STR
    * `4`: PHY
    * `10`: Super AGL
    * `11`: Super TEQ
    * `12`: Super INT
    * `13`: Super STR
    * `14`: Super PHY
    * `20`: Extreme AGL
    * `21`: Extreme TEQ
    * `22`: Extreme INT
    * `23`: Extreme STR
    * `24`: Extreme PHY
* `lv_max`
    * Type: `number, required`
    * Max level obtainable through normal training
* `skill_lv_max`
    * Type: `number, required`
    * Max super attack level
* `grow_type`
    * Type: `number, required`
    * Links to [card_growths](#card_growths) `grow_type` column
* `optimal_awakening_grow_type`
    * Type: `number`
* `price`
    * Type: `number, required`
    * Sell price
* `exp_type`
    * Type: `number, required`
    * Links to [exp_types](#exp_types) `exp_type` column
* `training_exp`
    * Type: `number, required`
    * Base exp when used as a training partner
* `special_motion`
    * Type: `number, required`
* `skill_id`
    * Type: `number`
* `passive_skill_set_id`
    * Type: `number`
    * Links to [passive_skill_sets](#passive_skill_sets)
* `leader_skill_id`
    * Type: `number`
    * Links to [leader_skills](#leader_skills)
* `link_skill1_id`
    * Type: `number`
    * Links to [link_skills](#link_skills)
* `link_skill2_id`
    * Type: `number`
    * Links to [link_skills](#link_skills)
* `link_skill3_id`
    * Type: `number`
    * Links to [link_skills](#link_skills)
* `link_skill4_id`
    * Type: `number`
    * Links to [link_skills](#link_skills)
* `link_skill5_id`
    * Type: `number`
    * Links to [link_skills](#link_skills)
* `link_skill6_id`
    * Type: `number`
    * Links to [link_skills](#link_skills)
* `link_skill7_id`
    * Type: `number`
    * Links to [link_skills](#link_skills)
* `eball_mod_min`
    * Type: `number, required`
* `eball_mod_num100`
    * Type: `number, required`
* `eball_mod_mid`
    * Type: `number, required`
* `eball_mod_mid_num`
    * Type: `number, required`
* `eball_mod_max`
    * Type: `number, required`
* `eball_mod_max_num`
    * Type: `number, required`
* `max_level_reward_id`
    * Type: `number`
* `max_level_reward_type`
    * Type: `text`
* `collectable_type`
    * Type: `number`
* `face_x`
    * Type: `number, required`
* `face_y`
    * Type: `number, required`
* `aura_id`
    * Type: `number`
* `aura_scale`
    * Type: `number`
* `aura_offset_x`
    * Type: `number`
* `aura_offset_y`
    * Type: `number`
* `is_aura_front`
    * Type: `boolean, required`
* `is_selling_only`
    * Type: `boolean, required`
    * Flag if unusable in a team
* `awakening_number`
    * Type: `number`
* `resource_id`
    * Type: `number`
    * If set, determines CPK file name of card assets. If unset, use  `id`.
* `bg_effect_id`
    * Type: `number`
    * If set, determines CPK file name of background effect assets. Usually used for LR rarity cards.
* `selling_exchange_point`
    * Type: `number, required`
    * Value of card in Baba points
* `awakening_element_type`
    * Type: `number`
* `potential_board_id`
    * Type: `number`
* `open_at`
    * Type: `date/time, required`
    * Hide card in game until this timestamp
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## characters

Description of `characters` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `race`
    * Type: `number, required`
* `sex`
    * Type: `number, required`
* `size`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## client_settings

Description of `client_settings` table.

**Columns:**

* `key`
    * Type: `text, required`
* `value`
    * Type: `text, required`
* `created_at`
    * Type: `date/time, required`
* `updated_at`
    * Type: `date/time, required`

  
  


## collection_categories

Description of `collection_categories` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `priority`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## collection_uniques

Description of `collection_uniques` table.

**Columns:**

* `id`
    * Type: `number, required`
* `collection_category_id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `priority`
    * Type: `number, required`
* `card_id`
    * Type: `number, required`
* `background_id`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## collection_cards

Description of `collection_cards` table.

**Columns:**

* `id`
    * Type: `number, required`
* `collection_unique_id`
    * Type: `number, required`
* `card_id`
    * Type: `number, required`
* `event_id`
    * Type: `number`
* `priority`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## effect_packs

Description of `effect_packs` table.

**Columns:**

* `id`
    * Type: `number, required`
* `category`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `pack_name`
    * Type: `text, required`
* `scene_name`
    * Type: `text, required`
* `red`
    * Type: `number, required`
* `green`
    * Type: `number, required`
* `blue`
    * Type: `number, required`
* `alpha`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## enemy_ai_conditions

Description of `enemy_ai_conditions` table.

**Columns:**

* `id`
    * Type: `number, required`
* `ai_type`
    * Type: `number, required`
* `action_type`
    * Type: `number, required`
* `weight`
    * Type: `number, required`
* `hp_rate_begin`
    * Type: `number, required`
* `hp_rate_end`
    * Type: `number, required`
* `min_interval`
    * Type: `number, required`
* `max_number`
    * Type: `number, required`
* `atk_rate_1`
    * Type: `number, required`
* `atk_rate_2`
    * Type: `number, required`
* `max_num_per_turn`
    * Type: `number, required`
* `recover_hp_rate`
    * Type: `number, required`
* `next_ai_type`
    * Type: `number`
* `ai_param`
    * Type: `number`
* `ai_param2`
    * Type: `number`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## enemy_skills

Description of `enemy_skills` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `description`
    * Type: `text`
* `exec_timing_type`
    * Type: `number, required`
* `turn`
    * Type: `number, required`
* `probability`
    * Type: `number, required`
* `causality_conditions`
    * Type: `text`
* `icon_type`
    * Type: `number, required`
* `target_type`
    * Type: `number, required`
* `target_value1`
    * Type: `number, required`
* `target_value2`
    * Type: `number, required`
* `target_value3`
    * Type: `number, required`
* `sub_target_type_set_id`
    * Type: `number, required`
* `efficacy_type`
    * Type: `number, required`
* `eff_value1`
    * Type: `number`
* `eff_value2`
    * Type: `number`
* `eff_value3`
    * Type: `number`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## eventkagi_items

Description of `eventkagi_items` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `description`
    * Type: `text, required`
* `rarity`
    * Type: `number, required`
* `area_tab_id`
    * Type: `number, required`
* `selling_exchange_point`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## forced_scripts

Description of `forced_scripts` table.

**Columns:**

* `id`
    * Type: `number, required`
* `script_id`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## recommend_special_views

Description of `recommend_special_views` table.

**Columns:**

* `id`
    * Type: `number, required`
* `card_id`
    * Type: `number, required`
* `view_id`
    * Type: `number, required`
* `created_at`
    * Type: `date/time, required`
* `updated_at`
    * Type: `date/time, required`

  
  


## related_card_categories

Description of `related_card_categories` table.

**Columns:**

* `id`
    * Type: `number, required`
* `enemy_skill_id`
    * Type: `number, required`
* `card_category_id`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## related_passive_skill_sets

Description of `related_passive_skill_sets` table.

**Columns:**

* `id`
    * Type: `number, required`
* `enemy_skill_id`
    * Type: `number, required`
* `passive_skill_set_id`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## related_link_skills

Description of `related_link_skills` table.

**Columns:**

* `id`
    * Type: `number, required`
* `enemy_skill_id`
    * Type: `number, required`
* `link_skill_id`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## helps

Description of `helps` table.

**Columns:**

* `id`
    * Type: `number, required`
* `help_category_id`
    * Type: `number, required`
* `num`
    * Type: `number`
* `title`
    * Type: `text, required`
* `description`
    * Type: `text`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## help_bodies

Description of `help_bodies` table.

**Columns:**

* `id`
    * Type: `number, required`
* `help_id`
    * Type: `number`
* `image_path`
    * Type: `text`
* `description`
    * Type: `text`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## help_categories

Description of `help_categories` table.

**Columns:**

* `id`
    * Type: `number, required`
* `num`
    * Type: `number`
* `title`
    * Type: `text, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## layout_permissions

Description of `layout_permissions` table.

**Columns:**

* `id`
    * Type: `number, required`
* `parts_name`
    * Type: `text, required`
* `status`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## leader_skills

Description of `leader_skills` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `description`
    * Type: `text, required`
* `exec_timing_type`
    * Type: `number, required`
* `efficacy_type1`
    * Type: `number, required`
* `efficacy_type2`
    * Type: `number, required`
* `efficacy_type3`
    * Type: `number, required`
* `efficacy_type4`
    * Type: `number, required`
* `efficacy_type5`
    * Type: `number, required`
* `target_type`
    * Type: `number, required`
* `sub_target_type_set_id1`
    * Type: `number, required`
* `sub_target_type_set_id2`
    * Type: `number, required`
* `sub_target_type_set_id3`
    * Type: `number, required`
* `sub_target_type_set_id4`
    * Type: `number, required`
* `sub_target_type_set_id5`
    * Type: `number, required`
* `calc_option1`
    * Type: `number, required`
* `calc_option2`
    * Type: `number, required`
* `calc_option3`
    * Type: `number, required`
* `calc_option4`
    * Type: `number, required`
* `calc_option5`
    * Type: `number, required`
* `causality_conditions`
    * Type: `text`
* `eff1_value1`
    * Type: `number, required`
* `eff1_value2`
    * Type: `number, required`
* `eff1_value3`
    * Type: `number, required`
* `eff2_value1`
    * Type: `number, required`
* `eff2_value2`
    * Type: `number, required`
* `eff2_value3`
    * Type: `number, required`
* `eff3_value1`
    * Type: `number, required`
* `eff3_value2`
    * Type: `number, required`
* `eff3_value3`
    * Type: `number, required`
* `eff4_value1`
    * Type: `number, required`
* `eff4_value2`
    * Type: `number, required`
* `eff4_value3`
    * Type: `number, required`
* `eff5_value1`
    * Type: `number, required`
* `eff5_value2`
    * Type: `number, required`
* `eff5_value3`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## level_bgs

Description of `level_bgs` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `bg1_enable`
    * Type: `number, required`
* `bg1_coef`
    * Type: `number, required`
* `bg1_flip_disable`
    * Type: `boolean, required`
* `bg2_enable`
    * Type: `number, required`
* `bg2_coef`
    * Type: `number, required`
* `bg2_flip_disable`
    * Type: `boolean, required`
* `bg3_enable`
    * Type: `number, required`
* `bg3_coef`
    * Type: `number, required`
* `bg3_flip_disable`
    * Type: `boolean, required`
* `bg4_enable`
    * Type: `number, required`
* `bg4_coef`
    * Type: `number, required`
* `bg4_flip_disable`
    * Type: `boolean, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## link_skills

Description of `link_skills` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `kana`
    * Type: `text`
* `description`
    * Type: `text, required`
* `need_link_num`
    * Type: `number, required`
* `link_check_type`
    * Type: `number, required`
* `efficacy_type`
    * Type: `number, required`
* `target_type`
    * Type: `number, required`
* `sub_target_type_set_id`
    * Type: `number, required`
* `influence_type`
    * Type: `number, required`
* `calc_option`
    * Type: `number, required`
* `turn`
    * Type: `number, required`
* `lnk_value1`
    * Type: `number, required`
* `lnk_value2`
    * Type: `number, required`
* `lnk_value3`
    * Type: `number, required`
* `eff_value1`
    * Type: `number, required`
* `eff_value2`
    * Type: `number, required`
* `eff_value3`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## marquees

Description of `marquees` table.

**Columns:**

* `id`
    * Type: `number, required`
* `scene_name`
    * Type: `text, required`
* `description`
    * Type: `text, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## mission_beginners_guides

Description of `mission_beginners_guides` table.

**Columns:**

* `id`
    * Type: `number, required`
* `beginners_guide_id`
    * Type: `number, required`
* `next_mission_id`
    * Type: `number, required`
* `description_script_id`
    * Type: `number`
* `description_image`
    * Type: `text`
* `banner_image`
    * Type: `text`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## mission_categories

Description of `mission_categories` table.

**Columns:**

* `id`
    * Type: `number, required`
* `type`
    * Type: `text`
* `name`
    * Type: `text, required`
* `required_rank`
    * Type: `number`
* `dragonball_session_id`
    * Type: `number`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## missions

Description of `missions` table.

**Columns:**

* `id`
    * Type: `number, required`
* `type`
    * Type: `text`
* `mission_category_id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `priority`
    * Type: `number, required`
* `orderer_id`
    * Type: `number, required`
* `description`
    * Type: `text, required`
* `target_value`
    * Type: `number, required`
* `conditions`
    * Type: `text`
* `area_id`
    * Type: `number`
* `z_battle_stage_id`
    * Type: `number`
* `start_at`
    * Type: `date/time, required`
* `end_at`
    * Type: `date/time, required`
* `end_at_hidden`
    * Type: `boolean, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## mission_rewards

Description of `mission_rewards` table.

**Columns:**

* `id`
    * Type: `number, required`
* `mission_id`
    * Type: `number, required`
* `item_id`
    * Type: `number, required`
* `item_type`
    * Type: `text, required`
* `quantity`
    * Type: `number, required`
* `card_exp_init`
    * Type: `number, required`
* `announcement_priority`
    * Type: `number`
* `announcement_label`
    * Type: `text`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## mission_campaigns

Description of `mission_campaigns` table.

**Columns:**

* `id`
    * Type: `number, required`
* `mission_id`
    * Type: `number, required`
* `campaign_id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## mission_periods

Description of `mission_periods` table.

**Columns:**

* `id`
    * Type: `number, required`
* `type`
    * Type: `text`
* `mission_id`
    * Type: `number, required`
* `wday`
    * Type: `number`
* `wday_start_at`
    * Type: `time`
* `wday_hours_to_end`
    * Type: `number`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## optimal_awakening_growths

Description of `optimal_awakening_growths` table.

**Columns:**

* `id`
    * Type: `number, required`
* `optimal_awakening_grow_type`
    * Type: `number, required`
* `step`
    * Type: `number, required`
* `lv_max`
    * Type: `number, required`
* `skill_lv_max`
    * Type: `number, required`
* `passive_skill_set_id`
    * Type: `number`
* `leader_skill_id`
    * Type: `number`

  
  


## passive_skills

Description of `passive_skills` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `description`
    * Type: `text, required`
* `exec_timing_type`
    * Type: `number, required`
* `efficacy_type`
    * Type: `number, required`
* `target_type`
    * Type: `number, required`
* `sub_target_type_set_id`
    * Type: `number, required`
* `influence_type`
    * Type: `number, required`
* `calc_option`
    * Type: `number, required`
* `turn`
    * Type: `number, required`
* `is_once`
    * Type: `boolean, required`
* `probability`
    * Type: `number, required`
* `causality_conditions`
    * Type: `text`
* `eff_value1`
    * Type: `number, required`
* `eff_value2`
    * Type: `number, required`
* `eff_value3`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## passive_skill_sets

Description of `passive_skill_sets` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text`
* `description`
    * Type: `text`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## passive_skill_set_relations

Description of `passive_skill_set_relations` table.

**Columns:**

* `id`
    * Type: `number, required`
* `passive_skill_set_id`
    * Type: `number, required`
* `passive_skill_id`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## points

Description of `points` table.

**Columns:**

* `id`
    * Type: `number, required`
* `type`
    * Type: `text`
* `amount`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## potential_items

Description of `potential_items` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `description`
    * Type: `text, required`
* `rarity`
    * Type: `number, required`
* `selling_exchange_point`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## potential_boards

Description of `potential_boards` table.

**Columns:**

* `id`
    * Type: `number, required`
* `comment`
    * Type: `text`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## potential_squares

Description of `potential_squares` table.

**Columns:**

* `id`
    * Type: `number, required`
* `potential_board_id`
    * Type: `number, required`
* `event_id`
    * Type: `number, required`
* `condition_set_id`
    * Type: `number, required`
* `is_locked`
    * Type: `boolean, required`
* `route`
    * Type: `number`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## potential_events

Description of `potential_events` table.

**Columns:**

* `id`
    * Type: `number, required`
* `type`
    * Type: `text, required`
* `currency_id`
    * Type: `number`
* `additional_value`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## potential_event_selection_tables

Description of `potential_event_selection_tables` table.

**Columns:**

* `id`
    * Type: `number, required`
* `comment`
    * Type: `text`
* `required_stone_for_unrelease`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## potential_event_selections

Description of `potential_event_selections` table.

**Columns:**

* `id`
    * Type: `number, required`
* `selection_table_id`
    * Type: `number, required`
* `event_id`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## potential_square_condition_sets

Description of `potential_square_condition_sets` table.

**Columns:**

* `id`
    * Type: `number, required`
* `comment`
    * Type: `text`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## potential_square_condition_set_relations

Description of `potential_square_condition_set_relations` table.

**Columns:**

* `id`
    * Type: `number, required`
* `condition_set_id`
    * Type: `number, required`
* `condition_id`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## potential_square_conditions

Description of `potential_square_conditions` table.

**Columns:**

* `id`
    * Type: `number, required`
* `type`
    * Type: `text, required`
* `conditions`
    * Type: `text`
* `comment`
    * Type: `text`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## potential_square_relations

Description of `potential_square_relations` table.

**Columns:**

* `id`
    * Type: `number, required`
* `potential_square_id`
    * Type: `number, required`
* `prev_potential_square_id`
    * Type: `number`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## potential_skills

Description of `potential_skills` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `description`
    * Type: `text, required`
* `exec_timing_type`
    * Type: `number, required`
* `efficacy_type`
    * Type: `number, required`
* `target_type`
    * Type: `number, required`
* `influence_type`
    * Type: `number, required`
* `calc_option`
    * Type: `number, required`
* `turn`
    * Type: `number, required`
* `is_once`
    * Type: `boolean, required`
* `probability`
    * Type: `number, required`
* `causality_conditions`
    * Type: `text`
* `eff_value1`
    * Type: `number, required`
* `eff_value2`
    * Type: `number, required`
* `eff_value3`
    * Type: `number, required`
* `variable_column`
    * Type: `text, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## potential_skill_lv_values

Description of `potential_skill_lv_values` table.

**Columns:**

* `id`
    * Type: `number, required`
* `potential_skill_id`
    * Type: `number, required`
* `lv`
    * Type: `number, required`
* `value`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## quests

Description of `quests` table.

**Columns:**

* `id`
    * Type: `number, required`
* `area_id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `prev_quest_id`
    * Type: `number`
* `any_clear_bonus_stones`
    * Type: `number`
* `all_clear_bonus_stones`
    * Type: `number`
* `icon_x`
    * Type: `number`
* `icon_y`
    * Type: `number`
* `visit_count_max`
    * Type: `number`
* `interval_reset_visited_days`
    * Type: `number`
* `can_ignore_difficulty_order`
    * Type: `boolean, required`
* `boostable`
    * Type: `boolean, required`
* `start_at`
    * Type: `date/time, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## quest_category_bonuses

Description of `quest_category_bonuses` table.

**Columns:**

* `id`
    * Type: `number, required`
* `quest_id`
    * Type: `number, required`
* `type`
    * Type: `text, required`
* `card_category_id`
    * Type: `number, required`
* `quest_category_bonus_rarity_table_id`
    * Type: `number`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## quest_category_bonus_groups

Description of `quest_category_bonus_groups` table.

**Columns:**

* `id`
    * Type: `number, required`
* `quest_category_bonus_type`
    * Type: `text, required`
* `name`
    * Type: `text, required`
* `description`
    * Type: `text`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## quest_category_bonus_rarity_tables

Description of `quest_category_bonus_rarity_tables` table.

**Columns:**

* `id`
    * Type: `number, required`
* `description`
    * Type: `text, required`
* `rarity_n`
    * Type: `number, required`
* `rarity_r`
    * Type: `number, required`
* `rarity_sr`
    * Type: `number, required`
* `rarity_ssr`
    * Type: `number, required`
* `rarity_ur`
    * Type: `number, required`
* `rarity_lr`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## rank_statuses

Description of `rank_statuses` table.

**Columns:**

* `id`
    * Type: `number, required`
* `rank`
    * Type: `number, required`
* `exp_total`
    * Type: `number, required`
* `act_max`
    * Type: `number, required`
* `team_cost_capacity`
    * Type: `number, required`
* `friends_capacity`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## rmbattle_bgm_patterns

Description of `rmbattle_bgm_patterns` table.

**Columns:**

* `id`
    * Type: `number, required`
* `normal_bgm_id`
    * Type: `number, required`
* `boss_bgm_id`
    * Type: `number, required`
* `last_boss_bgm_id`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## rmbattle_helps

Description of `rmbattle_helps` table.

**Columns:**

* `id`
    * Type: `number, required`
* `rmbattle_help_category_id`
    * Type: `number, required`
* `num`
    * Type: `number`
* `title`
    * Type: `text, required`
* `description`
    * Type: `text`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## rmbattle_help_bodies

Description of `rmbattle_help_bodies` table.

**Columns:**

* `id`
    * Type: `number, required`
* `rmbattle_help_id`
    * Type: `number, required`
* `image_path`
    * Type: `text`
* `description`
    * Type: `text`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## rmbattle_help_categories

Description of `rmbattle_help_categories` table.

**Columns:**

* `id`
    * Type: `number, required`
* `num`
    * Type: `number`
* `title`
    * Type: `text, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## rmbattle_missions

Description of `rmbattle_missions` table.

**Columns:**

* `id`
    * Type: `number, required`
* `rmbattle_id`
    * Type: `number, required`
* `type`
    * Type: `text, required`
* `name`
    * Type: `text, required`
* `priority`
    * Type: `number, required`
* `target_value`
    * Type: `number`
* `conditions`
    * Type: `text, required`
* `is_attention`
    * Type: `boolean, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## rmbattle_mission_rewards

Description of `rmbattle_mission_rewards` table.

**Columns:**

* `id`
    * Type: `number, required`
* `rmbattle_mission_id`
    * Type: `number, required`
* `item_id`
    * Type: `number, required`
* `item_type`
    * Type: `text, required`
* `quantity`
    * Type: `number, required`
* `card_exp_init`
    * Type: `number, required`
* `description`
    * Type: `text, required`
* `gift_description`
    * Type: `text, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## shops

Description of `shops` table.

**Columns:**

* `id`
    * Type: `number, required`
* `type`
    * Type: `text`
* `item_change_interval_sec`
    * Type: `number`
* `required_stone_to_change_item`
    * Type: `number`
* `open_at`
    * Type: `date/time, required`
* `close_at`
    * Type: `date/time, required`
* `start_at`
    * Type: `date/time, required`
* `end_at`
    * Type: `date/time, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## skills

Description of `skills` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `description`
    * Type: `text, required`
* `need_turn`
    * Type: `number, required`
* `efficacy_type`
    * Type: `number, required`
* `target_type`
    * Type: `number, required`
* `influence_type`
    * Type: `number, required`
* `calc_option`
    * Type: `number, required`
* `turn`
    * Type: `number, required`
* `eff_value1`
    * Type: `number, required`
* `eff_value2`
    * Type: `number, required`
* `eff_value3`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## skill_causalities

Description of `skill_causalities` table.

**Columns:**

* `id`
    * Type: `number, required`
* `causality_type`
    * Type: `number, required`
* `cau_val1`
    * Type: `number, required`
* `cau_val2`
    * Type: `number, required`
* `cau_val3`
    * Type: `number, required`
* `created_at`
    * Type: `date/time, required`
* `updated_at`
    * Type: `date/time, required`

  
  


## skill_groups

Description of `skill_groups` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `priority`
    * Type: `number, required`
* `created_at`
    * Type: `date/time, required`
* `updated_at`
    * Type: `date/time, required`

  
  


## skill_group_relations

Description of `skill_group_relations` table.

**Columns:**

* `target_type`
    * Type: `text, required`
* `target_id`
    * Type: `number, required`
* `skill_group_id`
    * Type: `number, required`
* `created_at`
    * Type: `date/time, required`
* `updated_at`
    * Type: `date/time, required`

  
  


## skill_labels

Description of `skill_labels` table.

**Columns:**

* `id`
    * Type: `number, required`
* `efficacy_type`
    * Type: `number, required`
* `is_display`
    * Type: `boolean, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## sound_effect_offsets

Description of `sound_effect_offsets` table.

**Columns:**

* `id`
    * Type: `number, required`
* `sound_effect_set_id`
    * Type: `number, required`
* `sound_effect_id`
    * Type: `number, required`
* `start_offset_millisecond`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## specials

Description of `specials` table.

**Columns:**

* `id`
    * Type: `number, required`
* `special_set_id`
    * Type: `number, required`
* `type`
    * Type: `text, required`
* `efficacy_type`
    * Type: `number, required`
* `target_type`
    * Type: `number, required`
* `calc_option`
    * Type: `number, required`
* `turn`
    * Type: `number, required`
* `prob`
    * Type: `number, required`
* `causality_conditions`
    * Type: `text`
* `eff_value1`
    * Type: `number, required`
* `eff_value2`
    * Type: `number, required`
* `eff_value3`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## special_bonuses

Description of `special_bonuses` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text`
* `description`
    * Type: `text`
* `efficacy_type`
    * Type: `number`
* `target_type`
    * Type: `number`
* `influence_type`
    * Type: `number`
* `calc_option`
    * Type: `number`
* `turn`
    * Type: `number`
* `probability`
    * Type: `number`
* `causality_conditions`
    * Type: `text`
* `eff_value1`
    * Type: `number`
* `eff_value2`
    * Type: `number`
* `eff_value3`
    * Type: `number`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## special_items

Description of `special_items` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text`
* `description`
    * Type: `text`
* `rarity`
    * Type: `number, required`
* `selling_exchange_point`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## special_scripts

Description of `special_scripts` table.

**Columns:**

* `id`
    * Type: `number, required`
* `script_name`
    * Type: `text, required`
* `attack_attributes`
    * Type: `number, required`
* `energy_color`
    * Type: `number`

  
  


## special_sets

Description of `special_sets` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `description`
    * Type: `text, required`
* `aim_target`
    * Type: `number, required`
* `increase_rate`
    * Type: `number, required`
* `lv_bonus`
    * Type: `number, required`
* `created_at`
    * Type: `date/time, required`
* `updated_at`
    * Type: `date/time, required`

  
  


## special_views

Description of `special_views` table.

**Columns:**

* `id`
    * Type: `number, required`
* `script_name`
    * Type: `text, required`
* `cut_in_card_id`
    * Type: `number, required`
* `special_name_no`
    * Type: `number, required`
* `special_motion`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## status_extensions

Description of `status_extensions` table.

**Columns:**

* `id`
    * Type: `number, required`
* `type`
    * Type: `text`
* `amount`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## sub_target_type_sets

Description of `sub_target_type_sets` table.

**Columns:**

* `id`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## sub_target_types

Description of `sub_target_types` table.

**Columns:**

* `id`
    * Type: `number, required`
* `sub_target_type_set_id`
    * Type: `number, required`
* `target_value_type`
    * Type: `number, required`
* `target_value`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## sugoroku_maps

Description of `sugoroku_maps` table.

**Columns:**

* `id`
    * Type: `number, required`
* `quest_id`
    * Type: `number`
* `difficulty`
    * Type: `number, required`
* `sugoroku_bgm_id`
    * Type: `number, required`
* `battle_bgm_id`
    * Type: `number, required`
* `boss_bgm_id`
    * Type: `number, required`
* `battle_background_id`
    * Type: `number, required`
* `act`
    * Type: `number, required`
* `eventkagi_num`
    * Type: `number, required`
* `user_exp`
    * Type: `number, required`
* `zeni`
    * Type: `number, required`
* `start_script_id`
    * Type: `number, required`
* `finish_script_id`
    * Type: `number, required`
* `first_focus_step`
    * Type: `number`
* `dice_id`
    * Type: `number`
* `clear_count_max`
    * Type: `number`
* `sugoroku_map_puzzle_color_id`
    * Type: `number, required`
* `is_cpu_only`
    * Type: `boolean, required`
* `danger_line_hp`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## sugoroku_map_puzzle_colors

Description of `sugoroku_map_puzzle_colors` table.

**Columns:**

* `id`
    * Type: `number, required`
* `weight_blue`
    * Type: `number, required`
* `weight_green`
    * Type: `number, required`
* `weight_purple`
    * Type: `number, required`
* `weight_red`
    * Type: `number, required`
* `weight_yellow`
    * Type: `number, required`
* `weight_rainbow`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## support_items

Description of `support_items` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text`
* `description`
    * Type: `text, required`
* `rarity`
    * Type: `number, required`
* `max_per_quest`
    * Type: `number`
* `max_per_quest_extended`
    * Type: `number`
* `efficacy_type1`
    * Type: `number, required`
* `efficacy_type2`
    * Type: `number, required`
* `target_type`
    * Type: `number, required`
* `calc_option`
    * Type: `number, required`
* `turn`
    * Type: `number, required`
* `eff1_value1`
    * Type: `number, required`
* `eff1_value2`
    * Type: `number, required`
* `eff1_value3`
    * Type: `number, required`
* `eff2_value1`
    * Type: `number, required`
* `eff2_value2`
    * Type: `number, required`
* `eff2_value3`
    * Type: `number, required`
* `ingame_type`
    * Type: `number, required`
* `selling_exchange_point`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## tips

Description of `tips` table.

**Columns:**

* `id`
    * Type: `number, required`
* `title`
    * Type: `text, required`
* `description`
    * Type: `text, required`
* `weight`
    * Type: `number, required`
* `image_name`
    * Type: `text`
* `start_at`
    * Type: `date/time, required`
* `end_at`
    * Type: `date/time, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## title_screens

Description of `title_screens` table.

**Columns:**

* `id`
    * Type: `number, required`
* `bg_anime`
    * Type: `text`
* `chara_anime`
    * Type: `text`
* `bgm_id`
    * Type: `number`
* `start_at`
    * Type: `date/time, required`
* `end_at`
    * Type: `date/time, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## transformation_descriptions

Description of `transformation_descriptions` table.

**Columns:**

* `id`
    * Type: `number, required`
* `skill_type`
    * Type: `text, required`
* `skill_id`
    * Type: `number, required`
* `description`
    * Type: `text, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## training_fields

Description of `training_fields` table.

**Columns:**

* `id`
    * Type: `number, required`
* `level_bg_id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `description`
    * Type: `text, required`
* `rarity`
    * Type: `number, required`
* `zeni`
    * Type: `number, required`
* `selling_exchange_point`
    * Type: `number, required`
* `exp`
    * Type: `number, required`
* `elements`
    * Type: `number, required`
* `multiplier`
    * Type: `number`
* `addend`
    * Type: `number`
* `card_training_field_exp_up_prob_id`
    * Type: `number`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## training_items

Description of `training_items` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `description`
    * Type: `text, required`
* `element`
    * Type: `number, required`
* `exp`
    * Type: `number, required`
* `rarity`
    * Type: `number, required`
* `zeni_to_use`
    * Type: `number, required`
* `selling_exchange_point`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## treasure_items

Description of `treasure_items` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `description`
    * Type: `text, required`
* `rarity`
    * Type: `number, required`
* `selling_exchange_point`
    * Type: `number, required`
* `image_suffix_number`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## ultimate_specials

Description of `ultimate_specials` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `description`
    * Type: `text, required`
* `increase_rate`
    * Type: `number, required`
* `created_at`
    * Type: `date/time, required`
* `updated_at`
    * Type: `date/time, required`

  
  


## wallpaper_items

Description of `wallpaper_items` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text`
* `description`
    * Type: `text`
* `created_at`
    * Type: `date/time, required`
* `updated_at`
    * Type: `date/time, required`

  
  


## worlds

Description of `worlds` table.

**Columns:**

* `id`
    * Type: `number, required`
* `name`
    * Type: `text, required`
* `prev_world_id`
    * Type: `number`
* `bgm_id`
    * Type: `number`
* `width`
    * Type: `number`
* `height`
    * Type: `number`
* `split`
    * Type: `number`
* `layer0`
    * Type: `text`
* `layer1`
    * Type: `text`
* `layer2`
    * Type: `text`
* `layer3`
    * Type: `text`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## z_battle_check_points

Description of `z_battle_check_points` table.

**Columns:**

* `id`
    * Type: `number, required`
* `z_battle_stage_id`
    * Type: `number, required`
* `level`
    * Type: `number, required`
* `act`
    * Type: `number, required`
* `eventkagi_num`
    * Type: `number, required`
* `z_battle_normal_reward_table_group_id`
    * Type: `number, required`
* `main_reward_id`
    * Type: `number`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## z_battle_enemies

Description of `z_battle_enemies` table.

**Columns:**

* `id`
    * Type: `number, required`
* `z_battle_stage_id`
    * Type: `number`
* `ordinal_num`
    * Type: `number, required`
* `start_level`
    * Type: `number, required`
* `end_level`
    * Type: `number`
* `base_hp`
    * Type: `number, required`
* `base_attack`
    * Type: `number, required`
* `base_defence`
    * Type: `number, required`
* `hp_escalation_type`
    * Type: `number, required`
* `attack_escalation_type`
    * Type: `number, required`
* `defence_escalation_type`
    * Type: `number, required`
* `special_attack_escalation_type`
    * Type: `number, required`
* `card_escalation_type`
    * Type: `number, required`
* `performance_escalation_type`
    * Type: `number, required`
* `skill_escalation_type`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## z_battle_enemy_card_escalations

Description of `z_battle_enemy_card_escalations` table.

**Columns:**

* `id`
    * Type: `number, required`
* `escalation_type`
    * Type: `number, required`
* `level`
    * Type: `number, required`
* `card_id`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## z_battle_enemy_skill_escalations

Description of `z_battle_enemy_skill_escalations` table.

**Columns:**

* `id`
    * Type: `number, required`
* `escalation_type`
    * Type: `number, required`
* `level`
    * Type: `number, required`
* `enemy_skill_id`
    * Type: `number`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## z_battle_enemy_status_escalations

Description of `z_battle_enemy_status_escalations` table.

**Columns:**

* `id`
    * Type: `number, required`
* `escalation_type`
    * Type: `number, required`
* `level`
    * Type: `number, required`
* `escalation_value`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## z_battle_first_rewards

Description of `z_battle_first_rewards` table.

**Columns:**

* `id`
    * Type: `number, required`
* `z_battle_first_reward_set_id`
    * Type: `number, required`
* `item_id`
    * Type: `number, required`
* `item_type`
    * Type: `text, required`
* `quantity`
    * Type: `number, required`
* `card_exp_init`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## z_battle_first_reward_level_ranges

Description of `z_battle_first_reward_level_ranges` table.

**Columns:**

* `id`
    * Type: `number, required`
* `z_battle_stage_id`
    * Type: `number, required`
* `level`
    * Type: `number, required`
* `z_battle_first_reward_set_id`
    * Type: `number, required`
* `main_reward_id`
    * Type: `number`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## z_battle_normal_reward_tables

Description of `z_battle_normal_reward_tables` table.

**Columns:**

* `id`
    * Type: `number, required`
* `z_battle_normal_reward_table_group_id`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## z_battle_normal_rewards

Description of `z_battle_normal_rewards` table.

**Columns:**

* `id`
    * Type: `number, required`
* `z_battle_normal_reward_table_id`
    * Type: `number, required`
* `item_id`
    * Type: `number, required`
* `item_type`
    * Type: `text, required`
* `quantity`
    * Type: `number, required`
* `card_exp_init`
    * Type: `number, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## z_battle_stages

Description of `z_battle_stages` table.

**Columns:**

* `id`
    * Type: `number, required`
* `z_battle_stage_effect_escalation_type`
    * Type: `number, required`
* `banner_image_path`
    * Type: `text`
* `listbutton_image_path`
    * Type: `text`
* `announcement_id`
    * Type: `number`
* `priority`
    * Type: `number, required`
* `danger_line_hp`
    * Type: `number, required`
* `start_at`
    * Type: `date/time, required`
* `end_at`
    * Type: `date/time, required`
* `locked_by`
    * Type: `text`
* `eventkagi_start_at`
    * Type: `date/time`
* `eventkagi_end_at`
    * Type: `date/time`

  
  


## z_battle_powerup_thresholds

Description of `z_battle_powerup_thresholds` table.

**Columns:**

* `id`
    * Type: `number, required`
* `z_battle_stage_id`
    * Type: `number, required`
* `hp`
    * Type: `number`
* `atk`
    * Type: `number`
* `def`
    * Type: `number`
* `special_atk`
    * Type: `number`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## z_battle_powerup_views

Description of `z_battle_powerup_views` table.

**Columns:**

* `id`
    * Type: `number, required`
* `enemy_skill_efficacy_type`
    * Type: `number, required`
* `texture_name`
    * Type: `text, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## z_battle_stage_levelup_views

Description of `z_battle_stage_levelup_views` table.

**Columns:**

* `id`
    * Type: `number, required`
* `stage_level`
    * Type: `number, required`
* `scene_name`
    * Type: `text, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`

  
  


## z_battle_stage_views

Description of `z_battle_stage_views` table.

**Columns:**

* `id`
    * Type: `number, required`
* `z_battle_stage_id`
    * Type: `number, required`
* `enemy_name`
    * Type: `text, required`
* `enemy_nickname`
    * Type: `text, required`
* `enemy_resource_id`
    * Type: `number, required`
* `params`
    * Type: `text, required`
* `created_at`
    * Type: `date/time`
* `updated_at`
    * Type: `date/time`
---
  
 