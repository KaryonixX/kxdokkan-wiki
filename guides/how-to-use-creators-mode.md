---
Title: How to use Creator's Mode?
Sort: 2
---
---
## What is Creator's Mode?

Creator's Mode is a feature in the UniDokkan patcher that allows fast iteration and testing before turning changes into a full Patch.

While made so that Creator's could have an easier way to test changes, this feature is created for everyone to use. It is the easiest way to make changes to the game assets/database without a rooted device.

<br /><br />
## How does it work?
Like any other application, Dokkan reads files from your device and uses them to run the game.

<img src="https://cdn.discordapp.com/attachments/528713422498562078/609578785498464257/GameUnderNormalOperation.png" width="800">

When Dokkan is run via the UniDokkan Patcher, the Patcher will intercept the game when it tries to open the database or open files. During this interception, the Patcher will give the game any patched files from enabled Patches.

<img src="https://cdn.discordapp.com/attachments/528713422498562078/609579098552926208/GameWhenRunViaPatcher.png" width="800">

 However, when Creator's Mode and Loose Loading is enabled, the Patcher will also give the game any files you designate as from a specified folder.
 
<img src="https://cdn.discordapp.com/attachments/528713422498562078/609578789235720242/GameWhenLooseLoading.png" width="800">

<br /><br />

## How to use Creator's Mode
### Enable Creator's Mode
1. Go into the options menu of the UniDokkan Patcher and navigate to the Creator's Mode settings.

	<img src="https://cdn.discordapp.com/attachments/528713422498562078/609578776723980288/FindOptionsMenu.png" width="400">
    
	<img src="https://cdn.discordapp.com/attachments/528713422498562078/609578777881739292/FindOptionsMenu2.png" width="400">
    
	<img src="https://cdn.discordapp.com/attachments/528713422498562078/609578782109597696/FindOptionsMenu3.png" width="400">
    <br /><br />
    
2. Turn on Creator's Mode. It will give you a warning about how Creator's mode can be dangerous. I recommend anyone developing patches to do so on non-main Dokkan accounts.

	<img src="https://cdn.discordapp.com/attachments/528713422498562078/609578771636551710/EnableCreatorsMode.png" width="400">
    
	<img src="https://cdn.discordapp.com/attachments/528713422498562078/609578773154889744/EnableCreatorsMode2.png" width="400">
    <br /><br />
    
3. Turn on one or more Creator's Mode options. We'll go over them next.

<br /><br />

### Creator's Mode Options

#### What is Loose Loading?
Loose loading allows you to replace the game assets and/or database without having to touch the game files. To use loose loading, you will designate a folder on your device that the game will load asset files and/or databases from. If you are using Nox, I recommend using the following folder for loose loading: `C:\Users\UserName\Nox_share\OtherShare` which in Nox will be `/mnt/shared/Other`.

<br /><br />

#### Enable Loose Loading
In the Creator's Mode settings in the Patcher, it will look like this:

<img src="https://cdn.discordapp.com/attachments/528713422498562078/609578824111226882/LooseLoadOptions.png" width="400">

1. First, turn on the `Load loose files` option.
2. Second, choose which folder on your device you want to load loose files from.
3. Third, you can optionally also choose to load a custom database file.

<br /><br />

#### Help Choosing a Folder

<img src="https://cdn.discordapp.com/attachments/528713422498562078/609578770549964800/ChoosingAFolder.png" width="400">

1. Press to go back up a folder
2. Press to go into a folder
3. Press to choose which folder you want to use
4. Press to confirm your selection

<br /><br />

#### How to use Loose Loading
You've enabled loose loading and selected a folder. For example, let's say you picked `/mnt/sdcard/Dokkan/` as your loose load folder.

**Loose loading a custom database** is simple. Place your modified database file in the folder. However, it must be named exactly `database.db`. From our example, your custom database will be located at `/mnt/sdcard/Dokkan/database.db`.

**Loose loading asset files** is only slightly more complicated. 
In this example, let's say you wanted to change the background for the card LR TEQ Broly.
* He has a `card_id` of `1016871`. 
* You have all the unpacked asset files, and you find the image you want to change, `character/card/1016870/card_1016871_bg.png`. 
* You edit this image, and now you want to loose load it. 

With loose loading enabled, the game will try and find this file in the folder you chose: 
```
/mnt/sdcard/Dokkan/
```
All you need to do, is add the file in the same place as it normally is, inside your choosen folder: 
```
/mnt/sdcard/Dokkan/character/card/1016870/card_1016871_bg.png
```
This means you must make a `character` folder inside your `Dokkan` folder. Then you make a `card` folder inside the newly created `character` folder. Then a `1016870` folder inside the newly created `card` folder. Finally, you place your edited `card_1016871_bg.png` in the newly created `1016870` folder.

__Note:__ It is recommended to only place files you change in the loose load folder.

<br /><br />

#### What is Logging?
Turning on logging has two benefits. 

 1. It allows you to see the file/folder paths that the game is trying to load assets from. 
 2. It allows you to get crash information. 

This information is invaluable for figuring out why your change crashed the game or is not working as you expected.

<br /><br />

#### Enable Logging

<img src="https://media.discordapp.net/attachments/528713422498562078/609578814112268309/LoggingOptions.png" width="400">

 1. Turn on the option `Save logs`
 2. Choose a folder where the logs will be saved, the same way as choosing a folder for loose loading.
 3. Turn on `Log file requests`
 4. Turn on `Log database requests`
 5. The game will now save log files, one for each time you run the game.
 
<br /><br />

#### Getting Additional Game Information

With Creator's Mode enabled, you can also get some relevant game information for making patches. 

<img src="https://cdn.discordapp.com/attachments/528713422498562078/609578768088170507/APKDetails.png" width="400">

<img src="https://cdn.discordapp.com/attachments/528713422498562078/609578769627480066/APKDetails2.png" width="400">

 - **Target APK** is the package name of the APK that the Patcher is currently targeting.
 - **Target APK Version** is the game version of the targeted game.
 - **Target Asset Version** is the version of the most recently downloaded assets. This number will be 0 if you have never completed a data download.
 - **Target DB Version** is the version of the most recently downloaded database. This number will be 0 if you have never completed a data download.

---