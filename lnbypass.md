---
layout: page
title: Local Network Bypass
permalink: /lnbypass/
nav_order: 2
---

**DISCLAIMER: This Bypass will expose your local server to the internet. That means anyone with your url can make requests to your server.**
**DO NOT SHARE YOUR URL WITH ANYONE. Entropy was not designed to handle multiple users or multiple connections. Also there is no DDOS protections in place so**
**PLEASE USE AT YOUR OWN RISK**

## Tunneling service

First you'll need to download and install a tunneling service. 
I highly recommend using [**ngrok**](https://ngrok.com/) There is a free tier that gets the job done.

Another service is [**local tunnel**](https://localtunnel.github.io/www/)
**DISCLAIMER As of writing this localtunnel's services are currently down. Therefore this tutorial will only cover ngrok**


Once you've downloaded ngrok, extract it. You should find a ngrok.exe there. 

Now start open the Dokkan Entropy exe and hit `[1] Start Server`. Choose your port or use the default.

Once the server has started, find the ngrok exe you extracted earlier. Copy the path to the exe.

Open a terminal and enter `cd` followed by the path to the ngrok exe. 

Next enter `ngrok http port` replace `port` with the port number your Entropy Server is serving on.
For example the default will be `ngrok http 8080`.
Ngrok will then give you a url that resolves to your server.
![ngrok](/imgs/ngrok.png)


Now Go to the settings app on your idevice and scroll down until you find the Dokkan Entropy app settings.
Select it then select Entropy PC Settings. In the hostname field Enter the url given to you by ngrok.
In the port field enter 443. This is the standard port for all https traffic.
![ngrokSettings](/imgs/ngrokSettings.png)

That's the bypass. With this you'll be able to play on cellular data or wifi from anywhere!

