---
title: Custom Audio Files - Legacy
Sort: 3
permalink: /custom-audio-legacy/
nav_order: 7
---
[**Thanks to T6 for allowing me to reuse the UD wiki!**](https://twitter.com/ThievingSix) 

[**Be sure to check out his new Dokkan Wiki**](https://dokkan.wiki/)

### [**Custom Audio Files by marcanin3**](https://twitter.com/TheMarcanin3)

## **Required Tools**
* [ADX Frontend](https://gamebanana.com/tools/6334)
* [AWB Unpacker/Repacker](https://steamcommunity.com/sharedfiles/filedetails/?id=632355452)
* [Degod](https://cdn.discordapp.com/attachments/1166527102837866506/1166527168940093541/degod.exe?ex=654ad016&is=65385b16&hm=f726965d577b7021d87098a87375be340eab34a4ebf491d377f8dbd1c9175e7d&)
* [SonicAudioTools (ACB)](https://github.com/blueskythlikesclouds/SonicAudioTools)
<br /><br />

## **Let's Begin**

This will be a quick tutorial on how to modify the audio files correctly, once i figure out each BGM/SE
stage or SFX they are assigned to, i will list them here.
<br /><br />
## **For AWB files**

In this example i will modify the title screen BGM (bgm_009.awb).

1. First of all you'll work around with WAV (Waveform Audio Format) files, so if your audio file 
is on another format you'll have to convert them into a WAV file.
 
2. Once you got your files ready it's time to make your files loop-able, for that you'll utilize *ADX Frontend*.

  Open *ADX Frontend*, and select your WAV file, after that check the "Looped Music" box, Starting Loop Point (in samples) is the start point where your audio file will start to play, Ending Loop Point (in samples) is where the loop will end, to know your sample rate use this formula:
  
  ```
  S * Hz=smp
  
  S = Current Song's time in seconds. (2mins is 180 seconds)
  
  H + is the Hertz of your song. (IE 48000Hz, 22050Hz, etc)
  
  So, if your song is 2mins 0secs (s180), your loop point beings at 32.450 seconds, and your Hz is 41000Hz, your start loop point would be
  
  32.450 * 41000 = 1,330,450smp
  End point would be end of the song or where the song repeats.
  
  180 * 41000 = 7,380,000 
  ```
  
  After it you'll end up ith an ADX file of your converted WAV, rename it to **00000000.adx** (this is only for BGM files).

3. Now we will use *Degod* to encrypt our ADX into the correct type, these are the option from *Degod* 
  ```
  Options:
          -k n    specify a key id (use -k ? for a list of keys)
          -s x -m x -a x  specify a key by components
          -M      mask out unused high bits (cannot be undone)
          -b      attempt to brute force a key
          -f n    first frame to brute force from
          -n n    number of frames to use in brutal attack
          -d 0|1  different keys per channel, do channel 0 or 1
          -o outfile.adx  output to a different file
                  (default is to modify original)
          -e      encrypt, rather than decrypt
          infile.adx      the ADX file to work with
  ```
  
  We will only work with "-k n" and "-e", **-k** is to specify the key Dokkan utilizes and know wich type of encryptation it uses, **-e** is to encrypt our file.
  
  Open the Command Prompt, drag n' drop *degod.exe* into it, type in "-k 9 (dokkan's id is 9) -e" you'll end up with something like this:
  
  ```path\degod.exe -k 9 -e```
        
    now simply just drag and drop your adx file and press enter, you'll end up with this:
    
  ``path\degod.exe -k 9 -e path/00000000.adx``
     
4. After you get your adx encrypted, just drag n' drop it into *AWB_repacker.exe*, you now will en up with an AWB file, **OUT.AWB**, rename it to the name of the BGM you are modifying (in this case bgm_009.awb).

5. Now you can place your new AWB file into the **bgm** folder from assets.


## **For ACB files**


1. Place your acb file on your SonicAudioTools folder, Drag n' Drop your ACB file into *AcbEditor.exe* (the Exe file not the xml file), you'll end up with a folder named the same as your ACB file.

2. Follow the steps from the AWB tutorial for your custom ADX files, you have to name it them the same name of the adx you are modifying (ex. 0001.adx)

3. After you have finished modifying ADX files, drag the folder into *AcbEditor.exe*, now you ACB is updated.

4. Now you can place your new AWB file into the **se** folder from assets.