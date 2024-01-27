---
Title: How to Create Patches
Sort: 1
---
**Valid as of:** Patch Version 2 — April 10th, 2019

UniDokkan patches are a custom file format that the UniDokkan Patcher temporarily applies to the game. Patches aren't permanent, and the game must be launched via the patcher for the patches to take effect.

The patch builder is web based and can be found on the UniDokkan website (Creators -> Patch Management -> Build Patch) at [https://unidokkan.com/creators/patches/build](https://unidokkan.com/creators/patches/build)

Patches are built from three types of files:

 1. SQL Files for Database changes
 2. Asset Files for Modified or new asset files
 3. Hook Files for Dokkan code modification

  

### SQL Files for Database changes
Changes to the database are done by adding SQL files to the patch list. SQL Files are a list of instructions that the patcher executes on the Dokkan database at game runtime.

The easiest solution to get SQL files is to edit the Dokkan database, then diff your results into a SQL files. Popular SQLite (with SQLCipher support) editors are: [DB Browser for SQLite](https://sqlitebrowser.org/) and [SQLiteStudio](https://sqlitestudio.pl/).

Once you have made the edits, you can go to the Database Diff tool (Creators -> Misc Tools). You give it the original unmodified database, and your edited one, and it will produce a `diff.sql` file that you can include in your patch.

If you are familiar with writing SQL, you are more than welcome to.

Once you have a SQL file, add it to the **`SQL Files`** section of the Patch Builder.
*(Currently there is a bug in which you are required to drag and drop the file to add it)*

  

### Asset Files for Modified or new asset files
Anything under the `assets/` directory of Dokkan can be replaced or added to. The only exception is the `database.db` file in which you use the SQL Files section.

In 99% of cases, you won't need to replace any `*.cpk` files directly. The packed files can be included individually.

When making a patch, create a folder structure that starts with `assets/`. When you add a file, create its appropriate location under `assets/`. If you are editing a file that is included in a CPK archive, you treat the file name of the CPK as a folder name *(without the `.cpk` extension)*.

For example: If you are only changing STR SSJ4 Goku's card background, you would make the following folder structure: `assets/character/card/1009420/`. In that folder you would add the modified `card_1009420_bg.png` file. Do not include any files that you did not edit. The only exception to this is if these files will be removed by Dokkan at a later date.

Audio Files (`*.acb` and `*.awb`) are archives for one or more ADX files. Unfortunately ADX files cannot be individually replaced by the patcher *(yet)*. To modify any audio, the entire archive must be patched.

Once you are done, add everything to the **`AssetFiles`** section of the Patch Builder that is under the `assets/` folder. Do not include the `assets/` folder. If in the upload list you see that your files start with `assets/`, your patch will not work.

  

### Hook Files for Dokkan code modification
Hook files are C++ libraries that will get loaded into the game at runtime. These libraries will be able to add, change, and remove game features.

Currently,  this feature is unavailable to Creators and is in its final testing phases. Once released it will be heavily reviewed and moderated to prevent abuse.

  

### Patch Info
To complete your patch, the following additional information is asked:

 - **Patch Name** — Try to keep it short but informative. This is what people see in their list of patches in the app.
 - **Patch Version*** — The patcher will track this version and let users know when updates are available. Read up on Semver for proper notation.
 - **Patch Description*** — A markdown enabled description of your patch. This will be shown on the website and in the patcher (after long press).
 - **Dokkan Regions** — A patch won't be able to be loaded for a certain region if that region is not checked.
 - **Dokkan APK Version*** — Allows you to lock your patch to a certain Dokkan version or a range of versions using a boolean operator. *Current information can be found under `Show APK Details` in the patcher.*
 - **Dokkan Asset Version*** — Allows you to lock your patch to a certain Dokkan asset version or a range of versions using a boolean operator. *Current information can be found under `Show APK Details` in the patcher.*
 - **Dokkan Database Version*** — Allows you to lock your patch to a certain Dokkan database version or a range of versions using a boolean operator. *Current information can be found under `Show APK Details` in the patcher.*
 - **Depends on*** — Allows you to select other UniDokkan patches that your patch relies on to work.


```
Items marked with '*' are currently not validated but will be used and enforced soon.
```

  

### Patch Building

Once everything is done (and all your files are uploaded), click **`Build Patch`**. If everything is right, your browser will download a patch file.

Eventually, you will be able to add the patch to the website directly. This will be required for the patches to work and be validated by the Patcher. 

**Currently**, the patch list is manually managed by me. However, you are welcome to post any patch to the `#patch-releases` channel in the UniDokkan Discord server.

  

### Notes

Excluding hooks, the only things we need to be careful of are modifcations of cards. As long as the card isn't significantly more powerful (2x is a good benchmark), the card's categories are not changed, and the card's typing isn't changed, it's usually safe. When the website is running in full, there will be a scoring system for the safety of the patch; for now, ask how safe a patch is before you release it and give users proper warnings.