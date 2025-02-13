---
title: "Daily driving a Linux Phone -  My Experience"
date: 2025-02-11
# weight: 1
tags: ["linux", "postmarketos"]
author: "Me"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: true
draft: false
hidemeta: false
comments: false
description: "My experience with mobile linux over the course of 3 years"
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: true
disableHLJS: false
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: images/linux-phone-experience.webp
    alt: "A photograph of 3 phones (Pinephone, Opeplus 6, Pixel 3a) running firefox on PostmarketOS displaying postmarketos.org" # alt text
    caption: "Many devices can run PostmarketOS" # display caption
---
My first exposure to 3rd-party smartphone operating systems originally intended to run Android was from a [Linus Tech Tip video](https://youtu.be/BsHtfLh6azw). This video covered how one could extend the usable life of an old smartphone by installing a 3rd-party Android ROM called [LineageOS](https://lineageos.org/). After further research, I also discovered a project called [Ubuntu Touch](https://devices.ubuntu-touch.io/) that promised to bring Ubuntu to your smartphone but in a touch-friendly package. While Ubuntu touch had an initial "wow" factor, this feeling eventually wore off when I realized that you can realistically only use app from the UBports app store, since desktop Ubuntu apps are pretty clunky to use on a small screen and do not support hardware acceleration on Ubuntu touch. 

This lead me searching for something that would let me run *Full*, *Fat*, *desktop* Linux apps on a smartphone, which is exactly the goal of [**PostmarketOS**](https://postmarketos.org): A true, linux operating system that uses an upstream, up to-date linux kernel and runs a Wayland or X11 compositor. Approaching smartphone software like this has several benefits:
* It reduces the need for new devices due to discontinuation of software, reducing ewaste.
* It improves privacy since no account is needed to use the device.
* There is no need to re-learn mobile-only software when your smartphone apps are the same as your desktop apps.

The biggest downside of PostmarketOS is hardware compatibility. Very few devices have working GPS, Camera or USB. This is why PostmarketOS has a handy [hardware table](https://wiki.postmarketos.org/wiki/Devices) that indicates a phone's hardware support for essential features.

![The PostmarketOS Table of hardware](images/pmos-table.png#center)


I concluded, based on the hardware table, that the [Pinephone](https://pine64.org/devices/pinephone/) , a phone designed to run Linux out of the box, was the best option. It has a working GPS, Camera, Video out, suspend and USB. The Pinephone's biggest weakness is that it uses a relatively old chip that uses lots of power (40nm transistor size!) for very weak performance. The interface is horribly sluggish and the battery lasts a bit over an hour when actively using it. I managed to daily drive it for almost a year, mostly since it's battery life when suspended was long enough to get though a day and not needing a case due to the plastic shell also helped.

![A photo of the Pinephone](images/pinephone.jpg#center)

After tolerating the Pinephone for a year, I looked for other options. I ended up picking up a [Oneplus 6](https://wiki.postmarketos.org/wiki/OnePlus_6_(oneplus-enchilada)) that I got for a reasonable price on [Kijiji](https://kijiji.ca), a local marketplace used in Ontario. The Oneplus 6 seems to be one of the best supported _Android devices_ that can run PostmarketOS. Cellular, haptics, speaker, and Graphical acceleration all function perfectly. There are a few major problems that hold this device back from perfection:
* _The camera is non functional._ I really enjoy having a camera on me at all times for personal use and I needed a camera for my job at the time (I solved this by carrying around a dedicated compact camera). Recently, there has been a [fork](https://gitlab.postmarketos.org/postmarketOS/pmaports/-/merge_requests/6148) of the kernel with preliminary camera support, but it lacks several core features, much like the pixel 3a that I will talk about.
* _The device will not wake from suspend for calls or SMS_, so suspend has to be disabled, though this is not much of a problem since the phone hardware is still able to last an entire day this way, and this also has the benefit of receiving internet notifications as well. 
* _No GPS_. (There is apparently a way to flash a specific android version to enable the GPS, I could not figure this out). Since I need a navigational device to navigate my city's nonsensical bike network, I used an old android phone for navigation.

![A photo of the Oneplus 6](images/oneplus.jpg#center)

Imagine how exited I was when I read the latest [PostmarketOS blog](https://postmarketos.org/blog/2024/08/25/pmOS-update-2024-08/) and found out the the camera on the [Pixel 3a](https://wiki.postmarketos.org/wiki/Google_Pixel_3a_(google-sargo)) was functional! I immediately looked to Kijiji again to see if I could find a Pixel 3a for a good price. I immediatly flashed the latest PostmarketOS Edge upon receiving it to see what the camera looked like. While I was impressed that a proper Linux phone had a working camera at all, the camera has a major issue that makes it almost useless to me: _There is no focus!_ The focus is locked to be as close as possible, so it's only really possible to take photos of small objects, like sharing your breakfast with friends. Even then, the photos have a green color to them and are cropped in, meaning the resolution and FOV of the phone camera is reduced. Looking at the [pmaports issue](https://gitlab.postmarketos.org/postmarketOS/pmaports/-/issues/3235) for cameras, it seems like lots of work is needed to get the camera backend to support focus at all, as well as actually getting the Pixel 3a hardware to work. The Pixel 3a had additional problems compared to the Oneplus 6 as well:
* Call audio would sometimes not work, and when it did, would only use the loudspeaker.
* The battery did not last long enough to last a day. I needed to charge midday to keep the phone running. (This could be due to a degraded battery, as the seller did warn me)

![A screenshot of using the camera on the Pixel 3a](images/sargo-cam-demo.jpg#center)

Overall, I really want to use PostmarketOS. The software does basically all I want out of a phone, and it does many thing better than Android. I really like how all the applications come from  central repository, meaning updates are at regular intervals. I like how notifications are only used to notify for communications. I like how I can sign into [Nextcloud](https://nextcloud.com/) and have Calender, Mail, Contacts and Files all work without dedicated sync applications or a different UX for each app. I like how the open applications stay in the order I left them. It's just that hardware support is lacking. 

I tried a project called [_Drodian_](https://droidian.org/), basically [Mobian](https://mobian-project.org/) running ontop of the original Android kernel using [Halium](https://halium.org/), but I found it to be prone to crashing and not connecting to cellular. As of writing this post, I use [CalyxOS](https://calyxos.org/que) on the Pixel 3a I got for PostmarketOS. It has a locked bootloader, working camera and GPS and All day battery. It just feels a bit icky to be using a Google OS with all the weirdness that Android entails when 90% of my needs are met my PostmarketOS.

I've considered the possibility of constructing my own phone using prefab components like a [RPI CM4](https://www.raspberrypi.com/products/compute-module-4/?variant=raspberry-pi-cm4001000), the [Qucetel Modem used in the pinephone](https://www.quectel.com/product/lte-eg25-g/), a Pi camera, 2 18650 cells, and a screen all joined by a custom PCB inside a 3d printed enclosure. While this device would probably be thick (~1.5-2.0cm) and would have poor specifications (Low res screen, short battery life), it could be possible to have everything just _work_, which would be enough for me.