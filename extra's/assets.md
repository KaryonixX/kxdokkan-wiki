---
title: Resources
Sort: 1000
---
[**Thanks to T6 for allowing me to reuse the UD wiki!**](https://twitter.com/ThievingSix) 

[**Be sure to check out his new Dokkan Wiki**](https://dokkan.wiki/)
## **Image Resolutions**

| Item | Resolution |
|------------|------------|
| card art | 426x568 |
| circle | 196x196 |
| thumb | 250x250 |
| piece | 74x88 |
| cutin | 852x266 |
| sp_cutin_1 | 1024x512 |

<sub>by BunRum</sub>


## **GUI**

This is a Zip Containing all the assets needed to make GUI's 

Note: for global compatibility just copy whatever is in the folder and put it for the available language folders
 
 [GUI](https://cdn.discordapp.com/attachments/565625878831169546/662005932871516170/Complete_GUI_Assets.zip)

<sub>By [GhostWaves](https://twitter.com/GhostKankitsu)</sub>


## **Templates**

<img src="https://cdn.discordapp.com/attachments/655235083745230848/733111487593316392/card_XXXXsp_cutin_1.png" width="350">

<!--- Dont Remove the previews please -->

<img src="https://cdn.discordapp.com/attachments/565625878831169546/625493536627884032/piece_template.png" width="100">

<!--- Dont Remove the previews please -->

<img src=https://cdn.discordapp.com/attachments/565625878831169546/625493535784960003/circle_template.png width="100">

<!--- Dont Remove the previews please -->

<img src=https://cdn.discordapp.com/attachments/565625878831169546/625493537764540438/thumb_1.png width="150">

<!--- Dont Remove the previews please -->

<sub>By BunRum</sub>

_________________________
## **Wallpaper template**

This *ZIP* file contains the files necessary for a STATIC image wallpaper, but nothing prevents you from making an animated wallpaper.
You will find 1 *.lwf*, 4 *.psd* and 1 *.json* file at the end of the *item* path.

<u>How to use and understand each file :</u>

- The **icon\_XXXX.psd** only contains a black image;
- The **thumb\_XXXX.psd** is a black rectangle with some transparent borders, you only need to put your image in the black rectangle and keep the transparent area;
- The **MyWallpaper.psd** has 2 layers to guide you :
	- The black area is what is NOT shown by the game ***on most phones***, but might on bigger screens such as tablets. Note that the screen of my phone is big (6.7 inches), so your phone might not show as high and as low as mine;
    - It also contains the interface of the main screen, so you can try and fit your wallpaper as you wish.
- The **info.json** contains 3 variables inside :
	- *theme* contains the name of the frame you want to use (list below);
    	- If you don't want to use any frame, set the variable to *null* without quotes.
    - *en* contains the english name of the wallpaper that will be displayed;
    - *fr* contains the french name of the wallpaper that will be displayed;
		- The engine will try to display the french name if you use the French Translation patch or if you play in french on Global. If it doesn't find it, it will use the english name.
    - You can also add some filler bars at the top and bottom if your wallpaper isnt big enough to fit big screens, only add this line under the theme variable:
    	- "filler":true,
- The **framename.psd** in `baou_wpadder\theme\` contains the basic frame and the ribbon of the basic frame. You can use it to make your own frames, just save it in this folder and give it any name; 
	- You can then use them in your patch exclusively if the name of the frame png is put in the *theme* variable of the **info.json** file.
- Note that you will need to change the **XXXX** in the names of the folder and files, but ***DO NOT*** rename the **MyWallpaper.png** and **info.json** files;
- The engine can detect **id**s from *1000 to 2000*, so the id you use for your wallpapers must be in this range or it won't show up in game.

<u>List of the frames included in the Engine:</u>

		- black
        - blue
        - gold (original frame)
        - green
        - purple
        - red
        - white
        - silver
        - rainbow

[Download Link of the ZIP](https://cdn.discordapp.com/attachments/655235083745230848/753044679586480178/TEMPLATE_ZIP.zip)

*If you are a creator, make sure to check the spreadshit posted in #knowledgebase to add your wallpapers to the list*

<sub>By [Energizz](https://twitter.com/_Energizz)</sub>