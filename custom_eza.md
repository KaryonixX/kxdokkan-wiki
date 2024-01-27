---
title: Beginner EZA Guide
permalink: /eza-guide/
nav_order: 5
---


---
If you want to learn more and interact with a community of modders join the [**dokkan modding community**](https://discord.gg/dokkanmods)



----
### A simple guide
This tutorial will cover the basics of an eza. It will not 
delve into complex passives,leader skills, and growths rather it will 
be simple enough for anyone to start creating eza's and
getting into the flow of dokkan modding. With that said 
lets begin


----
### Tools 

- [**Decrypted Databases**](https://dokkanentropy.com/modding/jp.db) (I will try to keep these updated on time)

SQLite3 database editor (Optional but recommended for beginners)

- [**DB Browser**](https://sqlitebrowser.org/) (Will be used in this tutorial) 
- [**SQLite Studio**](https://www.sqlitestudio.pl/)


Text Editor

- [**NotePad++**](https://notepad-plus-plus.org/) 
- [**VSCode**](https://code.visualstudio.com/) 


----

### Prerequisites

We will be dealing with the following database tables


- `cards` are the actual cards in the game.
- `card_specials` links a super attack to a card.
- `passive_skills` deals with the actual effects for passives. 
A cards passive is a collection of multiple rows in the `passive_skills` table
- `passive_skill_sets` deals with the text representation of a cards passive. This is displayed ingame
- `passive_skill_set_relations` This table links multiple `passive_skills` to a row in `passive_skill_sets`
a card is given a passive skill set and will have all the passive skills linked to that passive_skill_set determined 
by this table.
- `leader_skills` just like passive skills. This table deals with the actual effects of the leader skills. However it also has a link
to a leader skill set id. Think of it as `passive_skills` and `passive_skill_set_relations` in one table.
- `leader_skill_sets` This deals with the ingame representation of leader skills. It will be displayed with the card.

- `specials` Deals with the actual effects that occur when a card performs a super attack

- `special_sets` This is the ingame representation of Super Attacks. It will be displayed with the card.

- `optimal_awakening_growths` This is the table that contains all information regarding the eza has a link in the `cards` table

This table is beyond the scope of this tutorial but nonetheless are important and required for a eza

- `special_views` This contains the script name of the lua file that is executed before dokkan plays the special animation

For this guide I will be creating a eza for PHY Dokkan Fest Raditz.
I will be using DB Browser and VSCode


---



### How to make a EZA?


EZA's are fairly simple in nature. They are used to 
- Change a units Passive Skill
- Change a units Leader skill
- Change a units max level (Optional)
- Change a units Super Attack level

So lets take a look at raditz's card. I'll be using the [**dokkan wiki**](https://dokkan.wiki) to get all relative ids of the card
If you turn on developer mode you'll have access to all the id's related to the card.

Raditz's passive skill set id is `2808`. Lets search for his actual passive skills. Open the `passive_skills` table in your database editor of choice. I'll be using DB Browser as 
there are some convinent functions included. 

Filter the table by using the passive id of the card you've chosen. If needed filter the table futher by using the passive name.

Lets take a look at raditz's passive skills.
We can match the efficacy_type of each passive skill with the table on
the [**functions**](/functions/) page 

For our eza we're going to do a simple edit of increasing raditz's ATK & DEF boost of 150% to 200% and
increasing the ATK & DEF boost of 50% on super to 100%.

According to the functions table efficacy type 3 is ATK & DEF boost. 
We'll can see that Raditz's passive skill `2808` & `1002808` are both efficacy type 3.
So these are the two passives we will be copying and chaning. However keep track of the other passive id's
we'll be needing them for the future.
Highlight these rows and right click then select "Copy as SQL" as shown below

![passive](/imgs/passive_select.png)
Next open your text editor, create a new file then paste your sql.
It should look something like this 
```sql
INSERT INTO "main"."passive_skills" ("id", "name", "description", "exec_timing_type", "efficacy_type", "target_type", "sub_target_type_set_id", "passive_skill_effect_id", "calc_option", "turn", "is_once", "probability", "causality_conditions", "eff_value1", "eff_value2", "eff_value3", "created_at", "updated_at") VALUES ('2808', 'Raditz''s Enforcement', '自身のATKとDEF150%UP&敵が1体のとき必殺技発動時に更にATKとDEF50%UPし、必殺技発動時に敵のHPが50%以下のとき更にATK100%UPし、高確率で会心が発動&敵が2体以上のときは更にDEF150%UPし、攻撃を受けるとそのターン中、必ず会心が発動&敵にとどめを刺すとバトル中自身の気力+2', '1', '3', '1', '0', '', '2', '1', '0', '100', '', '150', '150', '0', '2022-09-30 11:44:04.438118', '2022-09-30 11:44:04.438118');
```


```sql
INSERT INTO "main"."passive_skills" ("id", "name", "description", "exec_timing_type", "efficacy_type", "target_type", "sub_target_type_set_id", "passive_skill_effect_id", "calc_option", "turn", "is_once", "probability", "causality_conditions", "eff_value1", "eff_value2", "eff_value3", "created_at", "updated_at") VALUES ('1002808', 'Raditz''s Enforcement', '自身のATKとDEF150%UP&敵が1体のとき必殺技発動時に更にATKとDEF50%UPし、必殺技発動時に敵のHPが50%以下のとき更にATK100%UPし、高確率で会心が発動&敵が2体以上のときは更にDEF150%UPし、攻撃を受けるとそのターン中、必ず会心が発動&敵にとどめを刺すとバトル中自身の気力+2', '4', '3', '1', '0', '', '2', '1', '0', '100', '{"source":"1388&1387","compiled":["&",1388,1387]}', '50', '50', '0', '2022-09-30 11:44:22.811827', '2022-09-30 11:44:22.811827');
```


You'll have the entire row translated to a SQL statement. It's best to turn the beginning of the statement
into a `INSERT OR REPLACE INTO` Statement rather than the default `INSERT INTO`. 


Now we'll change the passive id's of the SQL statement. We'll just add a prefix to the current id's. 
Ensure that this id is unique as it must be. The new id for the `2808` passive skill will be `7772808`
and the new id for the `1002808` will be `7771002808`.

Next we'll increase the ATK & DEF values
We know that the values are 150 & 50. So we'll change these values to 200, and 100 respectively

Now our SQL statements look like this
```sql
INSERT OR REPLACE INTO "main"."passive_skills" ("id", "name", "description", "exec_timing_type", "efficacy_type", "target_type", "sub_target_type_set_id", "passive_skill_effect_id", "calc_option", "turn", "is_once", "probability", "causality_conditions", "eff_value1", "eff_value2", "eff_value3", "created_at", "updated_at") VALUES ('7772808', 'Raditz''s Enforcement', '自身のATKとDEF150%UP&敵が1体のとき必殺技発動時に更にATKとDEF50%UPし、必殺技発動時に敵のHPが50%以下のとき更にATK100%UPし、高確率で会心が発動&敵が2体以上のときは更にDEF150%UPし、攻撃を受けるとそのターン中、必ず会心が発動&敵にとどめを刺すとバトル中自身の気力+2', '1', '3', '1', '0', '', '2', '1', '0', '100', '', '200', '200', '0', '2022-09-30 11:44:04.438118', '2022-09-30 11:44:04.438118');
```


```sql
INSERT OR REPLACE INTO "main"."passive_skills" ("id", "name", "description", "exec_timing_type", "efficacy_type", "target_type", "sub_target_type_set_id", "passive_skill_effect_id", "calc_option", "turn", "is_once", "probability", "causality_conditions", "eff_value1", "eff_value2", "eff_value3", "created_at", "updated_at") VALUES ('7771002808', 'Raditz''s Enforcement', '自身のATKとDEF150%UP&敵が1体のとき必殺技発動時に更にATKとDEF50%UPし、必殺技発動時に敵のHPが50%以下のとき更にATK100%UPし、高確率で会心が発動&敵が2体以上のときは更にDEF150%UPし、攻撃を受けるとそのターン中、必ず会心が発動&敵にとどめを刺すとバトル中自身の気力+2', '4', '3', '1', '0', '', '2', '1', '0', '100', '{"source":"1388&1387","compiled":["&",1388,1387]}', '100', '100', '0', '2022-09-30 11:44:22.811827', '2022-09-30 11:44:22.811827');
```


Next we'll copy raditz's SQL `passive_skill_set` statement. Go to the `passive_skill_set` table
then filter it to find the specific row, with our tutorial we'll be using the id `2808`. Then once we got the single row
highlight and copy it as SQL.
Now paste the sql into your text editor. 
It should look like this 

```sql

INSERT INTO "main"."passive_skill_sets" ("id", "name", "description", "created_at", "updated_at") VALUES ('2808', 'Raditz''s Enforcement', 'ATK & DEF +150%; plus an additional ATK & DEF +50% 
when performing a Super Attack if facing only 1 enemy and 
if that enemy''s HP is 50% or less when the character 
performs a Super Attack, plus an additional ATK +100% and 
high chance of performing a critical hit; performs a critical hit 
within the same turn after receiving an attack plus 
an additional DEF +150% when facing 2 or more enemies; 
Ki +2 for the rest of battle after delivering a final blow', '2022-09-30 11:43:49.006735', '2022-09-30 11:43:49.006735');

```

We'll change the id for the passive_skill_set statement from `2808` to `7772808`.
Then we'll change the percentages from 150% to 200% and 50% to 100%. 
So now our statement should looked like 

```sql

INSERT OR REPLACE INTO "main"."passive_skill_sets" ("id", "name", "description", "created_at", "updated_at") VALUES ('7772808', 'Raditz''s Enforcement', 'ATK & DEF +200%; plus an additional ATK & DEF +100% 
when performing a Super Attack if facing only 1 enemy and 
if that enemy''s HP is 50% or less when the character 
performs a Super Attack, plus an additional ATK +100% and 
high chance of performing a critical hit; performs a critical hit 
within the same turn after receiving an attack plus 
an additional DEF +150% when facing 2 or more enemies; 
Ki +2 for the rest of battle after delivering a final blow', '2022-09-30 11:43:49.006735', '2022-09-30 11:43:49.006735');

```

Finally we'll connect our passive skills and passive skill set using the `passive_skill_set_relations` table. 
So in your text editor write the following SQL for each passive skill changed. For this example the statements will be the following
```sql
INSERT OR REPLACE INTO passive_skill_set_relations VALUES (7772808,7772808,7772808,DATETIME('now'),DATETIME('now'));
INSERT OR REPLACE INTO passive_skill_set_relations VALUES (7772809,7772808,7771002808,DATETIME('now'),DATETIME('now'));
INSERT OR REPLACE INTO passive_skill_set_relations VALUES (7772810,7772808,2002808,DATETIME('now'),DATETIME('now'));
INSERT OR REPLACE INTO passive_skill_set_relations VALUES (7772811,7772808,3002808,DATETIME('now'),DATETIME('now'));
INSERT OR REPLACE INTO passive_skill_set_relations VALUES (7772812,7772808,4002808,DATETIME('now'),DATETIME('now'));
INSERT OR REPLACE INTO passive_skill_set_relations VALUES (7772813,7772808,5002808,DATETIME('now'),DATETIME('now'));
INSERT OR REPLACE INTO passive_skill_set_relations VALUES (7772814,7772808,6002808,DATETIME('now'),DATETIME('now'));

```

Notice that we used quite a few passive_skills id from raditz's originally passive. We've only modified two passives, so when linking to our new
passive skill set we still have to include the rest of the original passive.

Now then that covers the passive skill. This tutorial won't go into covering leader skills, super attacks, etc... However figuring it out shouldn't be too difficult.

Finally we must give raditz and actual eza. There are two statements we must add. First we must create a new row in optimal_awakening_growths table and then we must 
update the cards table to reflect the new row created. 

```sql
INSERT OR REPLACE INTO optimal_awakening_growths VALUES (789123,123789,7,140,15,7772808,102406);

UPDATE cards SET optimal_awakening_grow_type = 123789 WHERE id = 1024061;
```
So the first statement is creating a new row with a random id, and a random growth type. The next 3 values relate to the eza. For all urs use 7 and 140 entropy is hard coded to recognize these.
Finally we're linking our created passive_skill_set to the eza and raditz's previous leader_skill_set. If you did make a custom leader_skill_set then use that instead.
The second statement is updating the raditz's card to use the newly created growth type. Notice we didn't use the row id of the growth type but rather the actual id given to the type.

Thus with that your eza is complete. Rebuild your cards and box and you will see your changes in game.
Here is the complete script. If you've been following along yours should look identical. 
```sql

INSERT OR REPLACE INTO "main"."passive_skills" ("id", "name", "description", "exec_timing_type", "efficacy_type", "target_type", "sub_target_type_set_id", "passive_skill_effect_id", "calc_option", "turn", "is_once", "probability", "causality_conditions", "eff_value1", "eff_value2", "eff_value3", "created_at", "updated_at") VALUES ('7772808', 'Raditz''s Enforcement', '自身のATKとDEF150%UP&敵が1体のとき必殺技発動時に更にATKとDEF50%UPし、必殺技発動時に敵のHPが50%以下のとき更にATK100%UPし、高確率で会心が発動&敵が2体以上のときは更にDEF150%UPし、攻撃を受けるとそのターン中、必ず会心が発動&敵にとどめを刺すとバトル中自身の気力+2', '1', '3', '1', '0', '', '2', '1', '0', '100', '', '200', '200', '0', '2022-09-30 11:44:04.438118', '2022-09-30 11:44:04.438118');
INSERT OR REPLACE INTO "main"."passive_skills" ("id", "name", "description", "exec_timing_type", "efficacy_type", "target_type", "sub_target_type_set_id", "passive_skill_effect_id", "calc_option", "turn", "is_once", "probability", "causality_conditions", "eff_value1", "eff_value2", "eff_value3", "created_at", "updated_at") VALUES ('7771002808', 'Raditz''s Enforcement', '自身のATKとDEF150%UP&敵が1体のとき必殺技発動時に更にATKとDEF50%UPし、必殺技発動時に敵のHPが50%以下のとき更にATK100%UPし、高確率で会心が発動&敵が2体以上のときは更にDEF150%UPし、攻撃を受けるとそのターン中、必ず会心が発動&敵にとどめを刺すとバトル中自身の気力+2', '4', '3', '1', '0', '', '2', '1', '0', '100', '{"source":"1388&1387","compiled":["&",1388,1387]}', '100', '100', '0', '2022-09-30 11:44:22.811827', '2022-09-30 11:44:22.811827');
INSERT OR REPLACE INTO "main"."passive_skill_sets" ("id", "name", "description", "created_at", "updated_at") VALUES ('7772808', 'Raditz''s Enforcement', 'ATK & DEF +200%; plus an additional ATK & DEF +100% 
when performing a Super Attack if facing only 1 enemy and 
if that enemy''s HP is 50% or less when the character 
performs a Super Attack, plus an additional ATK +100% and 
high chance of performing a critical hit; performs a critical hit 
within the same turn after receiving an attack plus 
an additional DEF +150% when facing 2 or more enemies; 
Ki +2 for the rest of battle after delivering a final blow', '2022-09-30 11:43:49.006735', '2022-09-30 11:43:49.006735');
INSERT OR REPLACE INTO passive_skill_set_relations VALUES (7772808,7772808,7772808,DATETIME('now'),DATETIME('now'));
INSERT OR REPLACE INTO passive_skill_set_relations VALUES (7772809,7772808,7771002808,DATETIME('now'),DATETIME('now'));
INSERT OR REPLACE INTO passive_skill_set_relations VALUES (7772809,7772808,2002808,DATETIME('now'),DATETIME('now'));
INSERT OR REPLACE INTO passive_skill_set_relations VALUES (7772809,7772808,3002808,DATETIME('now'),DATETIME('now'));
INSERT OR REPLACE INTO passive_skill_set_relations VALUES (7772809,7772808,4002808,DATETIME('now'),DATETIME('now'));
INSERT OR REPLACE INTO passive_skill_set_relations VALUES (7772809,7772808,5002808,DATETIME('now'),DATETIME('now'));
INSERT OR REPLACE INTO passive_skill_set_relations VALUES (7772809,7772808,6002808,DATETIME('now'),DATETIME('now'));
INSERT OR REPLACE INTO optimal_awakening_growths VALUES (789123,123789,7,140,15,7772808,102406);
UPDATE cards SET optimal_awakening_grow_type = 123789 WHERE id = 1024061;

``` 

Congrats on your first eza! Cheers to many more to come! I can't wait to see what you creators create! 
Happy Modding!

