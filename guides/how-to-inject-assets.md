---
layout: page
title: Asset-Injection Guide
permalink: /inject-assets/
nav_order: 14
---

# How do we inject Custom Assets with the Proxy?

### *If you're on android you can just add files by transferring them to your phone and moving them into the asset directory at:*
### *Internal Storage: /Android/data/com.kary.kxcreator/files/*

If you're on iOS however, follow this guide.

First things first you need to download the [Injection-Host Tool.](https://discord.com/channels/794907952766255154/809530247225671680)
![**areadb](/imgs/dlserver.png)
This tool needs to stay open for the whole time that you're doing a custom DL or are just working with units in general.
Please have it in the same folder as your KX-Creator tool.

There will be also an assets folder in the same path created automatically.
Please put all your files into there, but you'll have to structure them similarly to how dokkan structures their Assets.
![**areadb](/imgs/assets.png)
You will want your database to be in the assets folder as follows:
- assets
    - sqlite
        - current
            - database.db
            `(encrypted with the DB Key: 2db857e837e0a81706e86ea66e2d1633)`

otherwise the hosting tool will not generate the asset sheet for the database and inject it.

___

## First time setup: ngrok
You will need to set up ngrok, which basically opens up your local filehost to a remote URL that you can use to download those assets onto your phone/emulator.

Download ngrok from [here](https://ngrok.com/download)
(Download for windows)

Afterwards you'll want to extract ngrok.exe to the same directory as your Creator-Tool and the other Host-Tool.
then you'll need to Sign up for [ngrok](https://dashboard.ngrok.com/signup) and get your authtoken after setting up 2fa.

![**areadb](/imgs/ngrokauth.png)

press WIN+R and enter `%localappdata%` and you should be taken to the local appdata folder.
make a new folder and name it ngrok, then create a file within that folder named ngrok.yml

Edit the file with a text editor and put your authtoken in the following way.:
```
authtoken: YOUR TOKEN HERE
```

now you'll want to open cmd in the same folder as the tools are in and type
`ngrok config upgrade`
which should set it all up for you.

Thats all with the setup!
___

Now you'll be able to use 
`ngrok http 8080`
in the same path as the tool
and it should be running
![**areadb](/imgs/ngrokrun.png)

copy the URL you see which is redirecting to your locally hosted server.

`https://example.ngrok-free.app`

![**areadb](/imgs/ngrokload.png)

now with all your assets in the folder and with the host-tool still running, we just insert that URL and press `Generate client_assets.json`
a loading bar should pop up, please wait until its done.

Now when its all done you should see `client_assets.json` and `database.json` (If you added a db to your assets path) in the same folder as the tool.

Now all we do is boot up the KX-Creator Tool/Proxy and if it asks us to enable File-Injection we allow that. 
It'll automatically add your stuff into the Data-Download whenever you trigger one. 

If you already have the latest data just hit `Clear Cache` in the middle of the Title Screen to trigger one.

And thats it!

After a while you should see that the Database and Assets are being Injected and you can actually keep track of the assets being downloaded.
![**areadb](/imgs/assetdl.png)
![**areadb](/imgs/dbdl.png)
