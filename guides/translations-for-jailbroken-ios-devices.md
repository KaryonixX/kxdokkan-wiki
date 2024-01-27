---
Title: Translations For Jailbroken iOS Devices
Sort: 99
---
---
### Unidokkan for iOS

<!-- In order to use any modifications on iOS you **must** be jailbroken. Using modifications for dokkan on iOS is more likely to be detected on iOS than it is using the Unidokkan patcher on Android. Any and all questions/concerns/issues should be directed at Xeno Vegito#6969 and **no other creators.** -->


# Starting Guide
In order to use any modifications on iOS you **must** be jailbroken. Using modifications for dokkan on iOS is more likely to be detected on iOS than it is using the Unidokkan patcher on Android. Any and all questions/concerns/issues should be directed at Xeno Vegito#6969 and **no other creators.**

The tweaks and repositories you will need installed on your device in order to use these mods. 

## Repositories

The repositories you will need to have downloaded are as follows:
<http://rpetri.ch/reposetup/>
<https://repo.rpgfarm.com/>

## Tweaks

**After** importing and downloading the repos to Cydia, the tweaks you will need are:
Filza File Manager (By TIGI Software)
AppList (By Ryan Petrich)
A-Bypass (By Baw Appie)


# Modding Begins

Once you have all the tweaks installed properly, open Filza and navigate to your root folder. From there navigate to the path /var/mobile/Containers/Data/Application/ and scroll until you find either the Dokkan Battle folder (for global) or the ドッカン folder (for jp). Once you are in that folder, navigate to Documents/assets/sqlite/current and copy the database.db file that is there. Make sure to paste it into a safe folder to make sure you have it to revert your dokkan to its original in case something goes wrong. Now, use the database.db file that you got from the Unidokkan Discord server, copy it, and paste it in:

```var/mobile/Containers/Data/Applications/[whichever Dokkan version you are using]/Documents/assets/sqlite/current```

When prompted to either rename or replace, pick the replace option. Now launch Dokkan, and whatever modification you downloaded should be there.
---