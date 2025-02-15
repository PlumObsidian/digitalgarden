---
{"dg-publish":true,"permalink":"/linux-applications-and-cheat-sheets/raspberry-pi/install-headless-plexamp-for-your-raspberry-pi-to-create-a-plex-endpoint/","title":"Install Headless Plexamp for your Raspberry Pi to create a Plex endpoint","tags":["clippings","raspberrypi","linux","audio","howto"]}
---

---
title: "Install Headless Plexamp for your Raspberry Pi to create a Plex endpoint"
source: "https://howtohifi.com/install-headless-plexamp-endpoint-home-network-raspberry-pi/"
author:
  - "[[How To Hi-Fi\|How To Hi-Fi]]"
published: 2024-11-02
created: 2025-02-15
description: "Use this guide to get started with Headless Plexamp using your Raspberry Pi. Stream your digital music library to any room in your home."
tags:
  - "clippings"
---
If you’re looking for a more music-focused app than what the standard Plex app provides, Plexamp is probably the answer. Plexamp is my go-to streaming app on my iPhone for many reasons.

The Plexamp app is polished, intuitively designed with a layout that doesn’t make you spend too much time trying to understand where to find settings, and it works perfectly for streaming [Bandcamp purchases I’ve added to my Plex server](https://howtohifi.com/bulk-download-your-entire-bandcamp-collection-with-batchcamp-chrome-extension/).

Plexamp also provides some features that are not typically found on other music streaming apps:

- Built-in EQ with a huge array of AutoEQ presets available
- Options to fine-tune the appearance of the app
- Gapless playback and Sweet Fades (really an amazing feature)
- [Sonic Explorations using OpenAI and Sonic Sage](https://howtohifi.com/how-to-use-plexamp-sonic-sage/)
- Built-in preamp
- Built-in Limiter
- Separate streaming quality and download options for WiFi and cellular

Really, the list goes on and on.

Even with all those options, setting Plexamp up the way I like is straightforward and quick. It’s just a very well-designed and well-built piece of software (not perfect, but pretty close).

If the cheeky notes sprinkled throughout the app are anything to go by, the Plex team has treated this project as a labor of love, and that love is further proven by their willingness to bring Plexamp to the Raspberry Pi in a headless configuration.

## Going headless with Plexamp

I run my [Plex server in a Headless configuration using a Raspberry Pi](https://howtohifi.com/how-to-install-your-plex-server-on-a-raspberry-pi-4-headless-edition/). This works seemlessly when using Plexamp from my iPhone, but it’s been a struggle to expand my network using Plexamp because, until very recently, Raspberry Pi users were limited to some very hacky methods of installing and using headless Plexamp with a Raspberry Pi.

Now that there is an official build from Plex it’s much more straight-forward to install and use Plexamp Headless, though it still took me a bit of trial and error to refine the process. This step-by-step guide is one way to get started with a Headless Plexamp Raspberry Pi project in the simplest terms possible.

If you’re new to headless Plex servers, Raspberry Pi computers, Terminal and command-line interface tools, I would recommend beginning with our [Complete Guide to creating a Headless Plex Server with Plexamp endpoints using a Raspberry Pi](https://howtohifi.com/a-complete-guide-to-creating-a-headless-plex-server-with-plexamp-endpoints-using-a-raspberry-pi/). Working through those articles in sequence will introduce you to the tools and concepts you’ll need to go Headless with Plex and Plexamp.

Once you have Plexamp installed on your Raspberry Pi you might want to enable updates for the software. To do that you’ll want to follow the steps we’ve documented in another post – [How to enable updates for Headless Plexamp on Raspberry Pi – get the latest Plexamp features](https://howtohifi.com/how-to-enable-updates-for-headless-plexamp-using-raspberry-pi/)

Follow the development of this essential add-on to your Plex Media service on [the Plexamp homepage](https://plexamp.com/) and read the changelog [at the Plex Forum.](https://forums.plex.tv/t/plexamp-release-notes/221280/49)

Here is a list of tools and equipment that you should have on hand before you begin this project:

### Supplies

- #### A Raspberry Pi 3 or 4

If you don’t have a Raspberry Pi handy, I would recommend [buying a Raspberry Pi 4 Starter Kit from CanaKit](https://www.canakit.com/). They offer a variety of kits, but each configuration will include everything you’ll need to get started. In writing this tutorial I’m using a Raspberry Pi 4 with 4GB of RAM, but I’ve read user reports that a Raspberry Pi 3B+ and up should work, and reports that 2GB of RAM is sufficient.

1. ## Install Raspberry Pi OS

If you’re following our [Complete Guide to creating a Headless Plex Server with Plexamp endpoints using a Raspberry Pi](https://howtohifi.com/a-complete-guide-to-creating-a-headless-plex-server-with-plexamp-endpoints-using-a-raspberry-pi/) you should already be familiar with Raspberry Pi Imager.

If you need a refresher on what Raspberry Pi Imager is and how to use it you should revisit the guide [A Beginner’s Guide to Installing Raspberry Pi OS.](https://howtohifi.com/beginners-guide-to-raspberry-pi-os-installation/)

For this guide I’m using **Raspberry Pi OS Lite (64-bit)**, but as of Plexamp 6.4.0 you can also use the 32-bit version of Raspberry Pi OS if you prefer.

In the advanced settings fill out all the necessary information. To keep things simple your username for this project should be ***pi.*** If your username is different there will just be an additional step to take.

After Raspberry Pi OS has been installed on your Micro-SD card you can insert it into your Raspberry Pi and power it on.

![Install Raspberry Pi OS](https://howtohifi.com/generated/assets/images/raspberry-pi-imager-app-700-945458b80.png)

Install Raspberry Pi OS

- [How to Install Raspberry Pi OS](https://howtohifi.com/beginners-guide-to-raspberry-pi-os-installation/)
2. ## SSH into your Raspberry Pi

With **Raspberry Pi OS** installed on your Micro-SD card and your Raspberry Pi powered on you’ll want to make sure you can SSH into the Pi.

If you’re following our [Complete Guide to creating a Headless Plex Server with Plexamp endpoints using a Raspberry Pi](https://howtohifi.com/a-complete-guide-to-creating-a-headless-plex-server-with-plexamp-endpoints-using-a-raspberry-pi/) you should already be familiar with how to SSH into your Raspberry Pi, but if you need a refresh you can visit the guide [How To SSH or Secure Shell into your Raspberry Pi](https://howtohifi.com/how-to-ssh-or-secure-shell-into-your-raspberry-pi/)

On your computer launch your command-line interface app (Terminal, in my case) and enter the following command, where **username** is the SSH username and **hostname** is the hostname you created in Raspberry Pi Imager:

`ssh username@hostname.local`

Then hit **Enter** and follow the prompts as you normally would.

![SSH into your Raspberry Pi](https://howtohifi.com/generated/assets/images/ssh-into-raspberry-pi-using-terminal-682-0b261f71d.png)

SSH into your Raspberry Pi
3. ## Update and upgrade your Raspberry Pi

Run the following command to ensure your Raspberry Pi Operating System is up to date:

`sudo apt-get update && sudo apt-get upgrade`

Sometimes this process can take a few minutes. As long as your Terminal window is still scrolling everything should be working as intended, but watch for prompts where you may need to acknowledge some installations and upgrades.

![Update and upgrade your Raspberry Pi](https://howtohifi.com/generated/assets/images/terminal-sudo-apt-get-update-and-upgrade-682-be51b9180.png)

Update and upgrade your Raspberry Pi
4. ## Use Terminal to Install Node js

As of Plexamp version 4.10 Headless Plexamp requires NodeJS 20 to run. It’s totally fine if you’re not familiar with Node JS, we’re just going to get it installed and then you likely won’t have to do anything with it again 😊

To install NodeJS 20, run the following commands in your Terminal window:

`sudo apt-get install -y ca-certificates curl gnupg && sudo mkdir -p /etc/apt/keyrings`

Hit **ENTER**

`curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg`

Hit **ENTER**

Then we’ll select version 20 with the following command:

`NODE_MAJOR=20`

Hit **ENTER**

Then:

`echo deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_$NODE_MAJOR.x nodistro main | sudo tee /etc/apt/sources.list.d/nodesource.list`

Hit **ENTER**

Then, finally run this command:

`sudo apt-get update && sudo apt-get install -y nodejs`

Hit **ENTER**

![Use Terminal to Install Node js](https://howtohifi.com/generated/assets/images/terminal-install-node-js-682-884d68b6a.png)

Use Terminal to Install Node js
5. ## Use Terminal to install Headless Plexamp

The Headless Plexamp package for Raspberry Pi is available [from the Plexamp website](https://plexamp.com/#downloads), but we’re going to use a curl command as a shortcut to grab and unzip the latest version directly into our Raspberry Pi.

Copy and paste the following command in terminal to download the Plexamp package:

`curl https://plexamp.plex.tv/headless/Plexamp-Linux-headless-v4.10.1.tar.bz2 > plexamp.tar.bz2`

Hit **Enter**

Now you can unzip the package with the following command:

`tar -xvf plexamp.tar.bz2`

Hit **Enter**

![Use Terminal to install Headless Plexamp](https://howtohifi.com/generated/assets/images/plexamp-curl-command-install-682-d54cc2fc5.png)

Use Terminal to install Headless Plexamp
6. ## Get your Plexamp token

To launch Plexamp for the first time you’ll need to get your token.

Enter this command in Terminal:

`node plexamp/js/index.js`

Hit **Enter**

Plexamp will start in the background.

In your browser navigate to [https://plex.tv/claim](https://plex.tv/claim) and copy the claim code presented.

Paste the claim code into your Terminal window.

Hit **Enter** then follow the prompt to name your player.

![Get your Plexamp token](https://howtohifi.com/generated/assets/images/plexamp-headless-claim-code-700-3a52cee6b.png)

Get your Plexamp token
7. ## Launch Plexamp in your browser

Then you’ll need to find the IP address for your Raspberry Pi. To do that, enter this command in Terminal:

`hostname -I`

Hit **Enter**

You’ll need to launch Plexamp again after the last step. To do that, enter this command in Terminal:

`node plexamp/js/index.js`

Hit **Enter**

Now, copy the IP address and navigate to the following address in your web browser:

`http://#.#.#.#:32500`

Replace the placeholder IP address in this example with your own and you should be presented with a screen to log in to Plexamp using your **Plex** Username and Password.

After entering your log in credentials you’ll be presented with some source options from your Plex server. Pick one to start with, you can easily change this later.

![Launch Plexamp in your browser](https://howtohifi.com/generated/assets/images/plexamp-welcome-to-plexamp-634-b790b9382.png)

Launch Plexamp in your browser
8. ## Check your Audio Settings and Select a Player

At this point you probably just want to start streaming. I’ve noticed that each time I set up a fresh Headless Plexamp install the intial audio stream will come out garbled and distorted, or won’t play at all.

If this happens to you, you may need to check a couple settings.

First, go to **Settings** → **Playback** → **Audio Output** → **Audio Device**

***If an Audio Device is already selected, de-select and re-select.*** I typically just select headphones here and have a quick listen to make sure music is streaming as expected.

Second, make sure you **Select a Player**.

In the top right corner of the browser, click on the *cast* icon. You should see the Player you’ve just created in addition to any other Plex endpoints. ***If a Player is already selected, de-select and re-select your new Player.***

Now have a listen 🎧

![Check your Audio Settings and Select a Player](https://howtohifi.com/generated/assets/images/plexamp-select-a-player-700-e349b7c9f.png)

Check your Audio Settings and Select a Player
9. ## Enable Plexamp to start automatically