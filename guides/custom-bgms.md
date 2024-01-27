---
title: Custom Bgms
Sort: 3
nav_order: 6
---

### [**Custom Bgms by freeoddity**](https://twitter.com/korewasosoruze)

## **Tools**
* [Radx Encode (Windows)](https://github.com/Isaac-Lozano/radx/releases/download/v0.3.1/radx_encode.exe)
* [Radx Encode (MacOS)](https://github.com/Isaac-Lozano/radx/releases/download/v0.3.1/radx_encode.exe)
* [AWB Unpacker/Repacker (Windows)](https://steamcommunity.com/sharedfiles/filedetails/?id=632355452)
* [AWB Repacker (MacOS)](https://cdn.discordapp.com/attachments/1166527102837866506/1166543521059192944/AWB_repacker?ex=654adf50&is=65386a50&hm=85cb5f7e65d4c7964ed03cce19181108e63c526b19225bf5b09da577a63cb7ea&)
* [AWB Unpacker (MacOS)](https://cdn.discordapp.com/attachments/1166527102837866506/1166543545331613777/AWB_unpacker?ex=654adf56&is=65386a56&hm=bc754d25432b579aff110d8076067658fcce50a99a454e8988a41587735a93b4&)
* [Degod (Windows)](https://cdn.discordapp.com/attachments/1166527102837866506/1166527168940093541/degod.exe?ex=654ad016&is=65385b16&hm=f726965d577b7021d87098a87375be340eab34a4ebf491d377f8dbd1c9175e7d&)
* [Degod (MacOS)](https://cdn.discordapp.com/attachments/1166527102837866506/1166527153416966169/degod?ex=654ad012&is=65385b12&hm=acc6878107269ea187b0667c14e0bed22d769240b55716a64048aebeed2bbc22&)
* [Audacity](https://www.audacityteam.org/)
<br /><br />

## **The Process**

There are 4 steps you must complete to create your own dokkan bgm *for now*. 
Those steps are the following:

* Obtain your audio source. This must be a **16 bit encoded wav** file with a sampling frequency no greater than 44khz

* Encode your wav into a adx file. We will be using Radx to accomplish this.

* Encrypt your adx using degod. We will use the 9th key setting to encrypt our adx.

* Package your adx file into a awb file. An awb file is simply a container used to hold other files.


## **Prerequisites**

Learn how to use terminal or command prompt. All the tools required by the process 
are command line applications. Meaning they have no graphical user interface (gui).
So practice using the command line or wait for the toolkit to contain the same features.

## **iOS**

The iOS Patcher of dokkan entropy is able to mass create bgms by completeing the process above.
Hit the Audio Creator Button in the patcher. Then select the Create BGMS popup. Next select all 
the wav files you'd like to convert to bgms. If you'd like to customize the loop points of the 
adx file, then simply select the tab associated with the wav file. It will spawn forth a popup 
allowing you to change the loop points used. Finally press the convert all files button in the top right
then patiently wait as the process commences. As long as your wav file meets the conditions laid out 
you will have a custom made bgm ready to be loaded ingame.

## **Windows/Mac**

# Encode a wav file into a adx file
Firstly, understand how to use radx. You may drag and drop your wav file into radx and by default 
you will obtain a loop encoded adx. The loop will start from the beginning of your wav file to the end of it.
If you want to set a custom loop point you must do so via cmd prompt/terminal. You can obtain your samples from 
audacity or follow the formula provided by the [legacy custom audio files](/custom-audio-legacy/) page. 
To start open a terminal in the same directory your radx program is and input source is. 

# Radx Examples
Imagine we're making a intro ost and we want to convert our `intro.wav` file into a adx with a custom loop point.
You can use radx via command line like this `radx -s 000000 -e 1234567 intro.wav intro.adx` 
What this is doing is starting the loop at sample 0 then ending the loop at sample 1234567.
Feel free to specify the input and output paths by providing the full or relative file paths.

# Encrypt adx
Now we take the output from radx and encrypt it. We've obtained a `intro.adx`.
Ensure the degod program is in the same directory as the `intro.adx` file. 
Then we'll use degod to encrypt it. We can use the command like so
`degod -k 9 -e intro.adx`
Note we used the 9th key becuase that key settings is the closest degod setting for dokkan's encryption
Also note we used the `-e` to tell degod we want to encrypt the adx
Finally we didn't specifiy an output file but you may. With our settings the `intro.adx` file
is overwritten with the encrypted version.

# Package into AWB
Finally you may simply drag and drop your encrypted adx file into AWB_repacker to obtain
a `OUT.AWB` file. Now all thats left is to simply rename your awb. For bgms dokkan uses the 
nomenclature where the bgm file is named `bgm_{id}.awb`. Simply replace the `{id}` substring 
with a numerical id. Note that AWB_repacker gave us a file with the extension `AWB` 
dokkan will fail to read this. Ensure that the extension is the lowercase`awb`. The id can be any number.
Then simply place it in the bgm folder of the assets.

# Conclusion
That is all, Enjoy adding your custom bgms to dokkan entropy!
The next audio tutorial will explain ACB's and their shenanigans!
Happy Modding Dokkaners!


