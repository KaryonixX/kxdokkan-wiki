---
layout: page
title: Custom Event Guide
permalink: /custom-events/
nav_order: 19
---

# How to create custom events with the KX-Creator tool?

First things first you need to select an Area-ID which hasnt been taken by anything in the game yet.

![**areadb](/imgs/areadb.png)

As you can see in this image, do not do what KX did in its early stages using Area IDs similar to Vanilla events as those get pushed out of the way as Dokkan adds new events.

You want to do it similarly to how the newer events are done. Select something with 5 digit IDs like 11001.
Now 11001 is the ID of your area and thus we need a SQL to Inject it with the Name.
(You select a different ID, check the db for whats currently not taken or ask other creators)

```
INSERT OR REPLACE INTO areas (id, type, category, world_id, name, area_icon_id,width,height,split, layer0,layer1,layer2,layer3,event_image_path,banner_image_path,minibanner_image_path,listbutton_image_path,is_listbutton_visible,event_priority,announcement_id, is_quest_num_visible,first_released_at,created_at,updated_at)
VALUES (11001,'Area::EventArea',12,1,'My New Event', 27,1500,1800,1,27,1,2,3,NULL,NULL, NULL, NULL, 1,1200,200821,1,'2022-01-29 06:00:00','2022-03-08 02:01:00','2022-03-08 02:01:00');
```

now we head to the `quests` table and see what stages we could add.

![**questsdb](/imgs/questsdb.png)

as we can see the `quests` table only has one entry for our Area-ID 11001
and that is 11001 + 001 = 11001001 (Area 11001, Stage 001)

Here is the SQL to add stages:
```
INSERT OR REPLACE INTO quests (id,area_id,name,prev_quest_id,any_clear_bonus_stones,all_clear_bonus_stones,visit_count_max,interval_reset_visited_days,can_ignore_difficulty_order,limitation_announcement_master_id,boostable,start_at,enable_sugoroku_auto,enable_battle_auto,created_at,updated_at) 
VALUES (11001001,11001,'Some Stage',NULL,1,NULL,NULL,NULL,1,NULL,0,'2015-10-30 00:00:00',0,0,'2024-04-15 01:20:09','2024-04-15 01:20:09');
```
Of course change this to reflect changes to your IDs.
you can copy and pase the same sql and only have to change the Stage-ID to give an event multiple stages.
for example:
```
INSERT OR REPLACE INTO quests (id,area_id,name,prev_quest_id,any_clear_bonus_stones,all_clear_bonus_stones,visit_count_max,interval_reset_visited_days,can_ignore_difficulty_order,limitation_announcement_master_id,boostable,start_at,enable_sugoroku_auto,enable_battle_auto,created_at,updated_at)
VALUES (11001002,11001,'Some Stage #2',NULL,1,NULL,NULL,NULL,1,NULL,0,'2015-10-30 00:00:00',0,0,'2024-04-15 01:20:09','2024-04-15 01:20:09');
```

And for every stage we just added we have to add a matching entry for the difficulty of the stage in the `sugoroku_maps` table.

![**sugoroku](/imgs/sugorokumapsdb.png)
as we can see every quest/stage now has its entry there consisting of
```
area-id + stage + difficulty
11001	+ 001	+ 5
```
which makes 110010015

difficulties go from Normal to Super3
```
0 = Normal,
1 = Hard,
2 = Z-Hard,
3 = Super,
4 = Super 2,
5 = Super 3
```
you can add many more things including the bgm/ost for the battle or map of the stage and the background that is shown during the fight.

here is the sql for sugoroku_maps:

```
INSERT OR REPLACE INTO sugoroku_maps (id,quest_id,difficulty,sugoroku_bgm_id,battle_bgm_id,boss_bgm_id,battle_background_id,act,eventkagi_num,user_exp,zeni,start_script_id,finish_script_id,first_focus_step,dice_id,sugoroku_map_puzzle_color_id,is_cpu_only,danger_line_hp,link_skill_lv_up_prob_rate,sugoroku_map_reward_group_id,created_at,updated_at)
VALUES (110010015,11001001,0,0,180,180,0,0,0,0,0,0,0,2,7,1,0,0,0.0,0,'2022-03-08 02:04:53','2022-03-08 02:04:53');
```
keep in mind for every stage you add, you also have to add a `sugoroku_maps` entry as the `quests` table entries directly link to it.

![**tool](/imgs/tool.png)
now we have to set up our tool the following way. 
the events.json has to reflect our Area-ID and Stages.
```json
{
    "events": [
        {
            "id": 11001,
            "announcement_id": 210399,
            "event_image": null,
            "banner_image": null,
            "minibanner_image": null,
            "listbutton_image": null,
            "recommend": null,
            "start_at": 0,
            "end_at": 9999999999,
            "wday": ["sunday","monday","tuesday","wednesday","thursday","friday","saturday"],
            "wday_start_at": 0,
            "wday_end_at": 9999999999,
            "lock": null,
            "quests": [
                {
                    "id": 11001001,
                    "name": "Some Stage",
                    "visit_count_max": null,
                    "interval_reset_visited_days": null,
                    "limitations": [{"id": 1,"type": "QuestLimitation::ContinueQuestLimitation::CountQuestLimitation","description": "No continues.","conditions": {"count_limit": 0}}]
                },
                {
                    "id": 11001002,
                    "name": "Some Stage #2",
                    "visit_count_max": null,
                    "interval_reset_visited_days": null,
                    "limitations": [{"id": 1,"type": "QuestLimitation::ContinueQuestLimitation::CountQuestLimitation","description": "No continues.","conditions": {"count_limit": 0}}]
                }
           ],
            "user_quest": {"visited_count": 0,"next_reset_at": 9999999999}
        }
    ]
}
```

as we can see the json has countless elements, but whats relevant for us is the ID of the Event.
that one is at the top *11001*

the event image is a file we replace with a link to our event image. Event images look like this:
![**tool](/imgs/quest_top_banner_11001.png)
they are exactly 852x610 pixels big.
Banner images are the scroll-wheel selection previews.
They look like this: 
![**tool](/imgs/quest_list_banner_11001.png)
they are exactly 600x120 pixels big.

You can drop images like this into a private discord channel and copy a link to the image.
That way you can host them through discord without having to worry about an external filestorage.
Make sure the Event-ID/Area matches and the quests are in the json-`quests`-object ("quests": [...])
you can add more events by adding a comma `,` after the quest before the last one and insert more stages
the objects are part of the list `[]`

Singluar Quest:
```json
{
    "id": 11001003,
    "name": "Stage Name #3",
    "visit_count_max": null,
    "interval_reset_visited_days": null,
    "limitations": [{"id": 1,"type": "QuestLimitation::ContinueQuestLimitation::CountQuestLimitation"description": "No continues.","conditions": {"count_limit": 0}
}
```

After we've got all of that set up we can move on to creating the Stages/Quests themselves.
Please name the jsons the same name as the Quests/Stage-IDs. So if its the first stage of the event 11001001 then the json matching it is 
11001001.json in the `inject_stages` folder.
___
```json
{
  "dummy_card_id": 1000780,
  "missions": [
    
  ],
  "sugoroku": {
    "dice": {
      "nums": [
        {
          "num": 1,
          "weight": 0
        },
        {
          "num": 2,
          "weight": 100
        },
        {
          "num": 3,
          "weight": 0
        },
        {
          "num": 4,
          "weight": 0
        },
        {
          "num": 5,
          "weight": 0
        },
        {
          "num": 6,
          "weight": 0
        }
      ]
    },
    "events": {
      "0": {
        "content": {
          "script_id": 0
        },
        "type": 501
      },
      "2": {
        "content": {
          "after_script_id": 0,
          "battle_info": [
            {
              "after_script_id": null,
              "background_id": 68,
              "before_script_id": null,
              "bgm_id": 98,
              "charge_limit": 0,
              "charge_limit_script_id": null,
              "round_id": 79003531
            }
          ],
          "battle_round_condition_sets": [
            
          ],
          "before_script_id": 0,
          "enemies": [
            [
              {
                "ai_type": 79,
                "attack": 600000,
                "card_id": 9108631,
                "defence": 400000,
                "enemy_round_skill_set_id": null,
                "enemy_skill_ids": [
                  33920,
                  33940,
                  33960,
                  33970,
                  34000
                ],
                "exp": 0,
                "extra_hp_gauges_count": 10,
                "finish_special_inform_hp": 0,
                "first_turn": 0,
                "hp": 150000000,
                "is_finish_special_only": false,
                "is_necessary_to_defeat": true,
                "multi_atk_num": 8,
                "turn": 0,
                "zeni": 0
              }
            ]
          ],
          "link_skill_lv_up": [
            
          ]
        },
        "type": 301
      },
      "4": {
        "content": {
          "script_id": 0
        },
        "type": 502
      }
    },
    "first_focus_step": 2,
    "map": "790_003"
  },
  "token": "lFg9lQ9jysLkUE+xec0idQ==",
  "user": {
    "achievement_id": 65,
    "act": 246,
    "act_at": 1706400598,
    "act_cure_shortened_sec": 10,
    "act_max": 246,
    "battle_energy": {
      "battle_at": 1679976434,
      "energy": 4,
      "max_recovery_count": 5,
      "recover_point_with_stone": 1,
      "recovered_count": 0,
      "seconds_per_cure": 10800
    },
    "boost_at": 1706500776,
    "boost_cure_shortened_sec": 240,
    "boost_point": 3,
    "card_capacity": 545,
    "exchange_point": 607570,
    "exp": 280269418,
    "friends_capacity": 100,
    "gasha_point": 1279400,
    "id": 698820203,
    "is_ondemand": false,
    "is_potential_releaseable": true,
    "is_support_item_capacity_extended": true,
    "mainpage_card_id": 1010851,
    "mainpage_user_card_id": 1338513867,
    "mydata_subpage_visible": false,
    "name": "Kary",
    "processed_at": 1706541622,
    "rank": 560,
    "stone": 3,
    "support_item_capacity": 4,
    "total_card_capacity": 1595,
    "tutorial": {
      "contents_lv": 500,
      "is_finished": true,
      "progress": 999
    },
    "wallpaper_item_id": 25,
    "zeni": 1551127720
  }
}
```

this is how one of those stages could look.
___

`dummy_card_id` This is the ID of a card the stage will use as dummys when the user hasn't filled his team. 

`dice[]` This contains all possible dice-rolls from 1 to 6 and the probability they come with. This stage has only the 2 button (100%)

`events` This is where you specify the tiles and what you'll encounter on them, i recommend using a Tile Map Editor like [Tiled](https://thorbjorn.itch.io/tiled)
After that you could open tmx files with it and preview how they're structured in order to get the Tiles info.

- `../sugoroku/tmx/AREAID.cpk` is usually the path of those and you can find them in your KX-Creator App's Asset Path.
After unpacking the CPK you should see all .tmx files for the stages of the Area.

![**tool](/imgs/tmx.png)

We've selected 790_003.tmx as our file, you can see it also matches our `map` tag in the json.
the important thing is that we see that its a linear map that starts at tile 0 and goes until tile 4.

The JSON has placed a 
- 501 / Start node at tile 0
- 301 / Enemy node with the enemy information at tile 2
- 502 / Finish node at tile 4
This means the event starts at tile 0, we fight our boss 2 tiles ahead and finish 2 more tiles after.

`content`->`battle_info[]`
    This block presents all "rounds" / phases of our event with their specific bgm, background and round id which can be whatever as long as its incremental.

`enemies[]` Here you can see a block that contains enemy information. For each phase we add a [] block. Within that block we can add anything from 1 to 5 enemies per phase `{},{},...` etc
Just make sure the amount of phases matches the amount of battle_info phases even if you have multiple enemies per phase.

(Dont copy and use this json, its been invalidated because of all the text and examples i added.)
```json
Example: Phase 1 with 1 enemy
        and phase 2 with 2 enemies.

"battle_info": [
            {
              "after_script_id": null,
              "background_id": 68,
              "before_script_id": null,
              "bgm_id": 98,
              "charge_limit": 0,
              "charge_limit_script_id": null,
              "round_id": 79003531 (790 03 5 Round 1)
            },
            {
              "after_script_id": null,
              "background_id": 72,
              "before_script_id": null,
              "bgm_id": 101,
              "charge_limit": 0,
              "charge_limit_script_id": null,
              "round_id": 79003532 (790 03 5 Round 2)
            }
          ]

"enemies": [
>            [ // Phase 1
              {
                any info in this block represents 1 enemy
              }
>            ], // Phase 1
>            [ 
              {
                any info in this block represents 1 enemy
              },
              {
                any info in this block represents 1 enemy
              }
>            ]
          ],
```

`enemies[]` -> `ai_type` Links to the database table `enemy_ai_conditions` and is responsible for enemy behaviour.

`enemies[]` -> `enemy_skill_id` links to the database table `enemy_skills` and is basically the "passive" of the enemy.

`enemies[]` -> `multi_atk_num` The amount of attacks the enemy will do. How many of it are supers is dependant on the ai_type.

`enemies[]` -> `extra_hp_gauges_count` This is purely visual, you can add up to 11 or 12 Extra HP Bars for the enemy to look intimidating.
- When you have multiple enemies per phase you want `extra_hp_gauges_count` to be 0 for all enemies because its purely visual.

`enemies[]` -> `is_necessary_to_defeat` This can either be `true` or `false`. This tells the game if that specific enemy is just a punching bag or is necessary to be defeated in order to complete the stage.
(Similar to the Zamasu and Goku Black Dokkan Event)

`enemies[]` -> `Other Stats` HP, DEF, ATK etc have to be adjusted by you to your liking, play around with them! They're easy to understand. 

THE REST OF THE JSON STAYS AS IS AND YOU'RE GOOD TO GO!

I recommend learning the [basics of JSON](https://www.youtube.com/watch?v=iiADhChRriM) in order to have a good time.
