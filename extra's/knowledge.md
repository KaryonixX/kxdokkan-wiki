---
title: UD Guides
Description: work in progress. Come back later
---
---
[**Thanks to T6 for allowing me to reuse the UD wiki!**](https://twitter.com/ThievingSix) 

[**Be sure to check out his new Dokkan Wiki**](https://dokkan.wiki/)
## **Custom Level**

In order to have a custom lvl like 420 all you have to do is add a new row in card_exps set lvl to desired lvl and set exp_type (to a random number above 999 or 4 trillion or a negative number) set exp_total to any number below 0 go to cards and set   exp_type to the number you set it to in card_exps table and set training_exp to the number you set it to in card_exps.exp_total and set lvl_max to the lvl amount you set it to in card_exps

<sub>by [BunRum](https://twitter.com/BunRum)</sub>

------------------------
## **Copy an existing Super Attack**


Get the view Id of that super and go to **specials\_views** <br>
In there search the id with the view id, it will appear a script name <br>
Now In the assets search the folder named Lua then inside that folder go to ab_script then attack\_sp <br>
Inside that folder search the script name and save the script (we'll need it for later)<br>
Now what you want to do is search the effects of the super in **effect\_packs** <br>

We'll need two things now : <br>
1)The id's from the scenes (to help with this just search the sp\_effect and the just search all rows with this sp\_effect)<br>
2)The assets of the super

Create a new sp\_effect folder that can be called anything and paste all the assets there (change the lwf name to the same as the folder)
Create the same amount of rows in the **effect\_packs** as the original and copy all things except the pack name and the id

In the pack name we'll put the name of our folder and in id it can be whatever that isn't used

Now we'll open the script from earlier (can be opened with notepad) and search the original IDs from effect\_packs and replace it with the new ones just created <br>
Change the name of the script to whatever you like and save

Now we just head up to the database and in special\_views we'll create a new row with any Id and in the script name we just put the name of the script we copied

And done! The Id in the row of **special\_views** will be used as a view id in the original super

<sub>from Rena & [Gokenn](https://twitter.com/zuhair_khatib)</sub>


------------------------
## **Super Attack Types**

`special_scripts.attack_attributes`

* 1 = **Ki based Super**

* 2 = **Melee based super**


------------------------
## **Element Types**


|Type|Neutral|Super|Extreme|
|----|-------|-----|-------|
|AGL |0      |10   |20     |
|TEQ |1      |11   |21     |
|INT |2      |12   |22     |
|STR |3      |13   |23     |
|PHY |4      |14   |24     |



------------------------
## **Type Bitsets**



|----|-----|
|AGL |1    |
|TEQ |2    |
|INT |4    |
|STR |8    |
|PHY |16   |
|Super |32 |
|Extreme |64 |
|Unknown |128 |
|Unknown |256 |
|Unknown |512 |
|Unknown |1024 |
|Unknown |2048 |                  
|Super AGL |4096 |
|Super TEQ |8192 |
|Super INT |16384 |
|Super STR |32768 |
|Super PHY |65536 |
|Extreme AGL |131072  |
|Extreme TEQ |262144  |
|Extreme INT |524288  |
|Extreme STR |1048576 |
|Extreme PHY |2097512 |
|Unknown |  4194304   |
|Unknown |  8388608   |
|Unknown |  16777216  |





------------------------
## **Leader Skills**

#### **Sub Target Types**

To create custom leader skills of category + category first you will need to go `sub_target_type_sets` and create 2 rows there, give them any id you want, then go to `sub_target_types` and create 3 rows with the first 2 having the **same sub\_target\_set\_id as one of the first row created earlier** one of those will have as **target\_ value\_type** 1 and **target\_value** will be the category id of the primary leader skill, the othe will have **target\_value\_type** 2 and the **target\_value** will be the category id of the secondary part of the leader skill , now, for the third row as the sub target set id you will set the id of the **second row you created earlier** and use **target\_value \_type** 1 and for the **target\_value** it will be once again the category id of the secondary part of the leader skill.

Now go back to your leader skill and set the sub target types set id's 1 and 2 as the first row you created in `sub_target_type_sets` and for the 3rd and 4th set id set it as the second row previously created in `sub_target_type_sets`.


#### **Leader Skill Efficacy**

**efficacy_type1** = 104

**efficacy_type2** = 5

**efficacy_type3** = 104

**efficacy_type4** = 5

**target_type** = 2

------------------------
* 
*eff1 corresponds to the first category you chose*

eff1_value1 = HP

eff1_value2 = ATK

eff1_value3 = DEF

------------------------
* 
*eff2 corresponds to the ki amount of the first category you chose*

eff2_value1 = Ki

eff2_value2 = 0

eff2_value3 = 0

------------------------
* 
*eff3 corresponds to the second category you chose*

eff3_value1 = HP

eff3_value2 = ATK

eff3_value3 = DEF

------------------------
* 
*eff4 corresponds to the ki amount of the second category you chose*

eff4_value1 = Ki

eff4_value2 = 0

eff4_value3 = 0


<sub>By Cake (Edited and fixed by Renacabeza26 and [Energizz](https://twitter.com/_Energizz))</sub>

------------------------
## **Super attack sa quote**

https://cdn.discordapp.com/attachments/565625878831169546/651216811844567041/unknown.png


id = The row id (use whatever isn't used)

script_name = lua script name

cut_in_card_id = pretty self-explanatory

special_name_no= sa quote/name stuff, if its 2 its the second one (xxx_sp02_phrase/name.png)

special_motion = determines which sprite sheet is used in the character folder

<sub>by Deo</sub>

------------------------
## **How to link an animation to a transformation**

How to link an animation to a transformation
If you already have the lwf and the images then it's easy
First you need to create a new folder in ingame/battle/effect/"New folder"
Its preferable to call it something like "Battle_00000"
00000 being any id you want
In that folder you will put the inages and the lwf
Now to link it go to effect_packs
Then create a row in effect_packs with any id and make the category 1
The name doesn't matter
And the pack name will be the same as the folder you created
And scene name will be ef_001
All the other things like blue red and those will be 255
Now in the battle params of the transformation link the idx 1 value with the effect pack id
And that's it

<sub>by Renacabeza</sub>

------------------------

## **Trident Requirements**

ID must be lower than 5000000 <br>
ID must not be between 2000000 and 4000000 <br>
awaked_card_id must be NULL <br>
Must have a potential board <br>
Must not have a great ape passive <br>
Must be open sooner than a year in the future. <br>

------------------------
## **Category id's**

1 = 	Fusion

2 = 	Shadow Dragon Saga

3 = 	World Tournament

4 = 	Peppy Gals

5 = 	Hybrid Saiyans

6 = 	Universe Survival Saga

7 = 	Resurrected Warriors

8 = 	Realm of Gods

9 = 	Majin Buu Saga

10 = 	Potara

11 = 	Low-Class Warrior

12 = 	Super Saiyan 3

13 = 	Giant Form

14 = 	Planet Namek Saga

15 = 	Ginyu Force

16 = 	Movie Bosses

17 = 	Pure Saiyans

18 = 	Namekians

19 = 	Future Saga

20 = 	Full Power

21 = 	Androids

22 = 	Representatives of Universe 7

23 = 	Transformation Boost

24 = 	Wicked Bloodline

25 = 	Dragon Ball Seekers

26 = 	Time Travelers

27 = 	Universe 6

28 = 	Joined Forces

29 = 	Movie Heroes

30 = 	Goku's Family

31 = 	Vegeta's Family

32 = 	Artificial Life Forms

33 = 	Youth

34 = 	DB Saga

35 = 	Siblings' Bond

36 = 	Super Saiyans

37 = 	Worthy Rivals

38 = 	Androids/Cell Saga

39 = 	Kamehameha

40 = 	Bond of Master and Disciple

41 =    Terrifying Conquerors

42 =    Dragon Ball Heroes 

43 =    Target: Goku

44 =    Otherworld Warriors

45 =    Super Saiyan 2

46 = 	Final Trump Card

47 =	Exploding Rage

48 = 	Revenge

49 = 	Team Bardock

50 = 	Inhuman Deeds

51 =    Earthlings

52 =	Special Pose

53 = 	Majin Power

54 = 	Rapid Growth

55 = 	All Out

56 = 	Universe 11

57 =	Saviors

--------------------------
## **Link Skill id's/Effects**

1 = 	Best Buddies/Ki +1

2 = 	Courage/Ki +1

3 = 	The Students/DEF +1000

4 = 	The Innocents/ATK +10%

5 = 	Crane School/ATK +500

6 = 	Demon/Ki +1

7 = 	Demon Duo/ATK +20%

8 = 	Brainiacs/ATK & DEF +10%

9 = 	Golden Warrior/Ki +1, enemy DEF -2000

10 = 	Money Money Money/Ki +1

11 = 	Evil Autocrats/Ki +1

12 = 	Flee/Ki +1 when HP is 30% or below

13 = 	Telekinesis/Enemy DEF -10%

14 = 	More Than Meets the Eye/ATK +300

15 = 	Hero/DEF + 20%

16 = 	Supreme Warrior/Ki +1

17 = 	Gentleman/Ki +2

18 = 	Brutal Beatdown/ATK +10%

19 = 	Messenger from the Future/ATK +500

20 = 	World Tournament Reborn/ATK +300

21 = 	New/ATK +200

22 = 	Saiyan Warrior Race/ATK +700

23 = 	All in the Family/DEF +15%

24 = 	Master and Pupil/Ki +1

25 = 	Respect/ATK +500

26 = 	Prodigies/ATK +10%

27 = 	World Tournament Champion/Ki +1

28 = 	Metamorphosis/Recover 5% HP

29 = 	Super Saiyan/ATK +10%

30 = 	Experienced Fighters/ATK +10%

31 = 	Twin Terrors/Ki +2

32 = 	Coward/Ki +1

33 = 	Attack of the Clones/Ki +1

34 = 	The Saiyan Lineage/Ki +1

35 = 	Android Assault/DEF +1000

36 = 	Turtle School/ATK +500, DEF+500

37 = 	Rival Duo/ATK +10%, attacked enemy's DEF -15%

38 = 	Mechanical Menaces/Ki +1

39 = 	Cold Judgment/DEF +20%

40 = 	Royal Lineage/Ki +1

41 = 	The Ginyu Force/ATK + 25%

42 = 	Infighter/ATK +10%, attacked enemy's DEF -10%

43 = 	Frieza's Minion/ATK +300

44 = 	Champion's Strength/Ki +1

45 = 	Z Fighters/ATK +15%

46 = 	Dodon Ray/ATK +2000 when Super Attack is launched

47 = 	Kamehameha/ATK +2500 when Super Attack is launched

48 = 	Namekians/Recover 5% HP

49 = 	Berserker/ATK +20% when HP is 50% or below

50 = 	Big Bad Bosses/ATK & DEF +25% when HP is 80% or below

51 = 	Frieza's Army/DEF +1000

52 = 	Tough as Nails/DEF +1500

53 = 	Speedy Retribution/ATK +300

54 = 	Tag Team of Terror/ATK +500

55 = 	RR Army/ATK +300

56 = 	Gaze of Respect/Ki +2

57 = 	Bombardment/ATK +15%

58 = 	Over 9000/ATK +10%

59 = 	Universe’s Most Malevolent/ATK +15%

60 = 	Shocking Speed/Ki +2

61 = 	Family Ties/Ki +2

62 = 	Team Bardock/Ki +1

63 = 	Saiyan Pride/ATK +15%

64 = 	Battlefield Diva/Ki +2

65 = 	Revival/Ki +2

66 = 	Dismal Future/Ki +1

67 = 	Organic Upgrade/Ki +2

68 = 	Resurrection 'F'/ATK +700

69 = 	Patrol/Ki +2

70 = 	Warrior Gods/ATK +10%

71 = 	Super-God Combat/ATK +15%

72 = 	New Frieza Army/ATK +1000, DEF +1000

73 = 	Loyalty/Ki +1

74 = 	Unbreakable Bond/Ki +2

75 = 	Galactic Visitor/Ki +1

76 = 	Master of Magic/ATK +15%

77 = 	Majin Resurrection Plan/Ki +2

78 = 	God of Destruction/ATK +1000

79 = 	Connoisseur/Recover 5% HP

80 = 	Godly Power/ATK +15%

81 = 	Energy Absorption/Ki +2

82 = 	Budding Warrior/ATK +10%

83 = 	Majin/ATK & DEF +10%

84 = 	Strength in Unity/Ki +1

85 = 	Strongest Clan in Space/Ki +2

86 = 	Thirst for Conquest/ATK +15%

87 = 	The Hera Clan/Ki +2

88 = 	Galactic Warriors/ATK +20%

89 = 	Over in a Flash/Ki +3

90 = 	The Incredible Adventure/Ki +2

91 = 	Coora's Underling/Ki +1

92 = 	Coora's Armored Squad/ATK +25%

93 = 	Hero of Justice/ATK +25%

94 = 	Signature Pose/Ki +2

95 = 	GT/Ki +2

96 = 	Infinite Regeneration/Recover 3% HP

97 = 	Prepared for Battle/Ki +2

98 = 	Destroyer of the Universe/ATK +25%

99 = 	Twin Fighters from Space/Ki +1

100 = 	Team Turles/Ki +1

101 = 	Fortuneteller Baba’s Fighter/Ki +2

102 = 	Guidance of the Dragon Balls/ATK +20%

103 = 	Power Bestowed by God/ATK +2500 when Super Attack is launched

104 = 	Hardened Grudge/Ki +1

105 = 	Auto Regeneration/Recover 3% HP

106 = 	Fusion/Ki +2

107 = 	Deficit Boost/ATK +15%

108 = 	Ultimate Lifeform/Ki +2

109 = 	Fierce Battle/ATK +15%

110 = 	Infinite Energy/Ki +2

111 = 	Formidable Enemy/ATK +10%

112 = 	Fused Fighter/Ki +2

113 = 	Fusion Failure/Recover 3% HP

114 = 	Scientist/Ki +2

115 = 	Hatred of Saiyans/Ki +2

116 = 	Limit-Breaking Form/ATK +2000 when Super Attack is launched

117 = 	The First Awakened/ATK +25%

118 = 	Shattering the Limit/Ki +2

119 = 	Nightmare/ATK +10%

120 = 	Fear and Faith/Ki +2

121 = 	Xenoverse/ATK +20%

122 = 	Super Strike/ATK +20%

123 = 	Transform/Ki +2

124 = 	Saiyan Roar/ATK +25%

125 = 	Legendary Power/ATK +5000 when Super Attack is launched

126 = 	Warriors of Universe 6/Ki +2

127 = 	Shadow Dragons/ATK +15%

128 = 	Penguin Village Adventure/ATK +15%

129 = 	Otherworld Warriors/ATK +20%

130 = 	Tournament of Power/Ki +3

1000 = 	Blazing Battle/Disables enemy's Rampage, and ATK +15%

1001 = 	Soul vs Soul/Weakens Regeneration and Ki +1

1002 = 	Golden Z-Fighter/Ki +2

1003 = 	Supreme Power/Activate Penetration, ATK & DEF + 1000

1004 = 	The Wall Standing Tall/Foils enemy's "True Power" and boosts ATK 
by 15%
---