---
Title: How To Create "Full Team" Patches
---
---

## How to Create "Full Team" Patches.
**How to create “Full Team” Patches.**

**Notes:** Before we start, I want to say that you NEED to use Trident with the Full Team Patch or Looseload for it to work. Otherwise, it will not show the duplicated units in your box. Also, NEVER lower the cost of the units.

**What is Trident?**

Trident Mobile is a Card Proxy tool using UniDokkan which allows the user to gain access to cards they do not have in order to use them in game. Locked/Favorited Units remain unchanged however will be boosted to Rainbow Stats while unlocked/non favorited units will be changed into the new and latest units while also being boosted to Rainbow Stats and Max Super Attack Level.

**Lets Begin:**

In this tutorial, I will show you all how to dupe the same unit multiple times and fit them under the same time where they will link perfectly with each other. I like to call these patches “Full Team” Patches.


You need to download the latest database version on either Global or the Japan version of the game. You can download the database in the #guides-tutorials channel on the UD discord server.

Create a text file and start testing to find 5 ID’s that are not already used in the database. These ID’s will be the ID’s used for the duped units. Once you find the 5 ID’s, type them all down in the text file so you don’t forget about them later on.
Go into the database using DB Browser or SQLite Studio. Go to the cards table and type down the ID of the unit you want to dupe in the search bar.

Once you find the unit that you want to dupe, highlight the 0 and 1 ID rows of the unit (which are the only 2 that there should be) and duplicate those rows 5 times. 5 times if you want 1 full team of the same unit but you can do more if you would like.

Once you duplicate those 2 rows 5 times, you change the ID’s of each row to the ID’s you typed down in the text document earlier. Example: 1090560 and 1090561 which are the duplicated rows have to be changed to 1040260 and 1040261. Remember that you must change the ID’s of both the 0 and 1 row.

After you change the ID’s of each row. You have to change the card unique info ID of each row to different numbers compared to the original unit’s card unique info ID. The card unique info ID determines if the same unit can be ran on the same team or not. If you change that to different ID’s, you will be allowed to run the same units on the same team.

Now, add the 0 version of the ID of the original unit to the bg_effect_ID and resource_ID of each row that was duplicated. This guarantees the correct card art showing for the duplicated units.

Now, we move onto the card_specials table. Look up the ID of the original unit in this table and then start duplicating the original rows about 5 times. You only have to change the ID of the duplicated rows to the 5 ID’s of the duplicated units.

Go to the table card_card_categories table and look up the ID of the original unit again. Once you find the rows, start duplicating all of them and start changing the ID’s of each of the rows to the ID’s of the duplicated units. Now, you will get an error at times while duplicating where the 1st row of the set of rows you duped, the card_category_ID and number of the category will be gone. This is easy to fix, just copy the card_category_ID and number from the original first row of the set and paste it into the duplicated row of the duplicated set. Make sure to duplicate ALL the rows for both the 0 and 1 version of the ID.

Once you finish duplicating all the category rows, if the unit does not have an active skill, you can diff it and make it into a patch or looseload it. Make sure to enable Trident Mobile with the patch or looseload or else the duplicated units will NOT appear in your box for you to use.

**Active Skill Step:**

11. If you the unit has an active skill, you have to go to the card active skills table and find the rows of the original ID of the unit. Then, you have to duplicate the rows and change the ID’s to the duplicated unit ID’s. After that, you’re finished.

**By TheRaven003.**
---