---
layout: post
title:  "The $49* ThinkPad T440P"
date:   2022-02-14
categories: thinkpad
---
![stinky](https://github.com/tiduscrying/tiduscrying.github.io/raw/main/_images/t440p/Snipaste_2022-02-14_16-15-51.png)

_*actually it ended up costing quite a bit more than that_

# How We Got Here (Prelude)
If you found this blog post, you probably already know how awesome old ThinkPads are. The easily replaceable parts, solid build materials and really nice official hardware guides make the line of laptops a personal favorite of mine. There is just something incredibly _sexy_ about older ThinkPads that few modern laptops come close to recapturing. The fact that these thick beasts can continue being fully functional almost 8-10 years later whereas some modern laptops become e-waste at 3 is just simply incredible. 

A few years ago I refurbished a T440S for my girlfriend and gave it to her for school. At the time, I had set it up as a Mojave Hackintosh with Clover. Fast-forward a few years and she eventually purchased a new M1 MacBook Pro since she needed an _actual_ Mac for work that would be a lot more reliable than something pasted together with glue and config files. Understandable. Realizing she didn't need it anymore, I figured I would bring it back with me and mess with it some more. 

The first thing I swapped out was the well-hated "Clunkpad". This was a bit of a bitch to get taken care of (and was no different on the T440P, either), but was overall worth it. The original trackpad kind of sucks and has softer, almost scissor-key like switches arranged in a 2x2 grid instead of a traditional clicking mechanism. The actual right/left click buttons were now more just "zones" that really did not feel satisfying to use. Even with the TrackPoint still being present, the lack of those physical buttons on the top of the trackpad as well meant it just felt really gross to use no matter how you wanted to use it.

Clunkpad replaced, I figured I would toss in a M2. SATA SSD and install a fresh copy Arch Linux onto it. This was _kind_ of a disaster in of itself. I ended up ordering a "KingShark *GAMING* SSD" for $70 since it had pretty favorable reviews and was a compatible with the M2 SATA 2240 slot inside the T440S. After attempting and failing to install Arch from scratch using the `archinstall` command, I moved on to EndevourOS which more or less worked. At some point, I decided I wanted to try BRTFS as the file system, and for _some reason_ the whole DRIVE went tits up after that. The BIOS no longer saw the SSD at all and spat out an error about the drive being un-usable. Chalking it up to maybe a bad drive, I ordered a replacement off Amazon and tried again only for the same issue to happen. At this point, I decided to forget about the drive, but in doing research to fix the problems of the T440S, seeing artciles and videos on the T440P... _really_ caught my eye. The way I saw it, the T440P just had so much _more_ fiddling potential.

Pretty much scrapping the stuff I had done with the T440S entirely, I put the original clunkpad back in it, installed Windows 10 pro and gave it to a family member to worry about. 
A day or so on eBay and I saw **the listing**. The _ultimate_ listing. No display, no keyboard, no HDD, no RAM. Sold AS-IS with a broken display. $49 + $20 shipping, "Buy It Now". The perfect project laptop for me to waste the next few weeks (and a decent chunk of change on) on. **Sold**. 

# Nothing Goes According To Plan
To get the show started for my new T440P, I went ahead and ordered some replacement parts that I knew I would need based on the eBay listing. I used the _excellent_ Octoperf guide about the T440P [here](https://octoperf.com/blog/2018/11/07/thinkpad-t440p-buyers-guide) along with the convenient Lenovo Hardware Manual and FRU list to source things. Among the first batch of things was a 1080P replacement panel (I decided to go with the N140HCE-EN1 Rev. C2 due to its lower power consuption), an 8GB stick of DDR3L RAM, and a backlit English keyboard (Made by Chicony; FRU 04x0139). I wanted to add a few additional things such as USB-C charging, and an upgraded processor so I went ahead and ordered those items as well. 

Few days pass and the parts start trickling in, first with the new display and keyboard, finally followed by the unit itself. Despite such a low asking price and the missing parts, it was in decent enough shape and was packaged quite nicely. No major scratches or scuffs on the housing, no chipped or peeling coatings, and all of the screws and internal stuff was in-tact (aside from the HDD caddy). The ThinkPad logos on both the lid and palm wrest even still had their original plastic covering the metal decals!

After replacing the display, installing the new RAM and SSD (instead of the KingShark Gaming drive, I went with a more well-known brand and got a Transcend 256GB drive instead. I also ditched the idea of doing anything BTRFS related for the time being) and seating the new keyboard I fired the machine on for the first time and got... _5 beeps_... This... Was not good. I knew this was not good. 5 Beeps? _5 beeps?_ The lights on the keyboard and power button would come on no problem, and even the CPU fan kicked on after a bit, but I was getting absoutely _nothing_ on the display. I tried a few things at first, mostly just re-seating the RAM and SSD. Trying the other slot for the RAM, without the SSD entirely, then eventually with neither to see if the beep-code would change. Nada. 

I did some digging and got worried pretty quickly. 5 beeps, according to all the threads I found and even Lenovo's documentation, pointed towards an issue with the motherboard. I felt immediately defeated before any of the real fun even began. I told myself it was no big deal since I didn't spend a whole lot on it yet _anyways_, but I still felt dumb for buying something I couldn't guarantee worked in the first place. 

I thought of a few solutions that could fix the issue without confronting the idea that the motherboard was toast entirely just yet. I ordered a replacement CMOS battery and main battery off Amazon. After installing the CMOS battery, I looked up ways to possibly try and get a signal from the laptop, but didn't have much luck. I thought about maybe trying to recover the BIOS using something like "WINCRISIS", but any attempts at that I saw online were vague and out-dated, usually ending in the original poster saying they either couldn't get it working or that they just gave up all together. At this point, I had only tried getting a VGA signal out of the laptop and didn't have any mini-display port adapters on hand to try. Given that I didn't get any signal through VGA, I ditched the idea of an external display and resumed just trying to get any signal at all on the replacement panel. My next options were becoming increasingly clear; either get a replacement motherboard, try a new CPU or attempt to recover the BIOS using an external flasher. I did with all three. 

# Recovering the BIOS
![stinky](https://github.com/tiduscrying/tiduscrying.github.io/raw/main/_images/t440p/PXL_20220113_041901083.jpg)

Now in the past, I've modified BIOSes before. I just really didn't like it because of how finnicky I found it. The first time I did this was with my first-ever ThinkPad (an X220) that I wanted to hackintosh. I did it all over again with a X230 about a year later (but ended up using ivyrain after my flasher started being annoying). I had also modified the BIOS of that old T440S to allow for non-whitelisted Lenovo wireless cards for MacOS. I recall the process for the T440S being a bit dodgy... Pretty much I had to dump the BIOS using an external programmer and send it to a guy through a BIOS modding forum to get it taken care of. It wasn't the most legit way to do things, but the site was discussed a lot and plenty of people were in the same thread with success stories, so I went ahead and PM'ed the fellow. Got my modified BIOS probably not even 30 minutes later and proceeded to flash. It worked and I sent the guy a tip for his services. 

Fast forward to now, apparently BIOS Modding for things like the wireless card whitelist removal has become well documented and doable to just about anyone with an external flasher. Not knowing whether or not the BIOS was corrupted with my motherboard, I attempted to dump it using my X230. Problem is, my CH341a flasher worked, but the little clips used to latch onto the BIOS chip had become quite loose and weren't getting a solid enough connection. Multiple, frustrating attempts at getting the chip to read in both Windows and Linux proved unsuccessful. I was soon losing confidence in myself, but knew I also had the replacement motherboard and processor on the way, so if I truly beefed things up I could still move on. 

I also ordered some replacement clips off Amazon and tried again a few days later. To my surprise, it worked immediately! Way better than the clips I had before, plus it was _also_ a two pack. I dumped the BIOS twice and verified my dumps -- both of them matched. I tried to figure out how to get a clean version of the BIOS installed, given that I couldn't get any video. First thing I tried was to download the most recent BIOS off Lenovo's site and extract the BIOS files. This got a bit messy and I am not going to confidently say I understand everything I was trying. At one point I was trying to extract BIOS "blobs" to compare to my dump and see if I could replace parts of it or just flash the new one as-is. That didn't end up working and I was getting very annoyed. There weren't any super well documented recovery stories online either. I saw one thread with a person in a similar situation trying to extract a clean BIOS from Lenovo's updater and succeeding, but they didn't go into much detail.

Eventually, I got a dangerous idea. Remembering those sites with people requesting whitelist removals, I found a few people that opted to just upload their BIOS dumps in the thread itself instead of sending them directly to someone. I knew it was a long shot and might not work, but I downloaded some random dump of someone's T440P and proceeded to flash it. Flashing externally always kind of struck me as _true hacker shit_, so I was very anxious whether or not it would work, but hoped it would because of how baddass it would feel to overcome a problem like this. Flash successfully went through and then... 

**_Nothing_.** 

I was no longer stuck getting just 5 beeps, but I still had no video out and nothing seemed to be responding. The fan was still kicking on and would eventually slow down, but nothing appeared to be different than before. I felt... Frustrated. So close, yet somehow still so far. I gave up for the time being and came back to the project a day or two later after purchasing a Mini Displayport to HDMI adapter. 

I plugged everything in to my main monitor and _it actually fucking worked!_ 

So what the hell was going on with the display? Did I somehow maybe short something? Did the motherboard have liquid damage or something, or was the video cable messed up? I attempted taking the entire laptop apart to inspect _everything_, but never considered the most obvious thing; the replacement display itself. Sure enough, I took the bezel off the display and inspected the plug and BEHOLD! The cable connecting the motherboard to the new panel itself wasn't even plugged in! I felt _so stupid_, but also relieved. At some point in reassembling the top half of the laptop, the cable must have gotten loose and unseated itself. Something this simple staring me in the face this whole time just goes to show that you always have to slow down and think about the simple stuff. 

After reseating the connection and securing it with some electrical tape, I put the bezel back on and everything was working as intended. First _massive_ hurdle overcome, but still plenty of little bumps in the road to come. At this point, I am curious if the BIOS was truly broken beforehand or not. For all I know, maybe I was getting _some_ sort of signal to the panel, but couldn't see it because it was unplugged? That being said, it worked now so I stopped worrying about it and kept going. 

Next order of business was to install an OS and get the flashed BIOS up-to-date. I started with just basic Windows 10 on the new SSD. The flashed BIOS I had downloaded was version `2.56`, but Lenovo was already up to `2.77`. Apparently they have been supporting the T440P with updates to vulnerabiliies for quite some time, which is nice to see. Luckily, the update went without issues and everything appeared to be working in the OS. At this point, the  replacement motherboard I had ordered in desparation set to arrive in the mail in a few days, but I felt as if messaging the seller and trying to send it back wouldn't be worth it at this point. The replacement board wasn't _too_ expensive and I figured having a spare would be convenient if things went south again.

To my genuine surprise, the model I had was the variant with a discrete Nvidia 730M GPU. I had read beforehand that this model was "not worth it" due to the poor performance overall of the 730M compared to the Intel HD graphics and additional drawbacks that came from having a discrete GPU. The replacement motherboard I had on the way appeared to be one without the Nvidia GPU, so I had my options if things didn't work out with this board. Windows 10 detected all of the hardware devices and Lenovo's System Updater made short work of fetching  updates. 

Updating the BIOS was simple enough. After downloading the normal executable off Lenovo's site, all I had to do was run it and wait for the laptop to reboot. After that, it went back into Windows and was working without a hitch.

With a renewed confidence in myself and now knowing that my BIOS flasher could work wonders, I decided I wanted to proceed with dumping the good BIOS and removing the BIOS whitelist myself. I figured having a backup of the known working BIOS as it was now would be beneficial if something else went wrong. Luckily, the process to removing the whitelist and enabling the "advanced menu" for the T440P is incredibly well documented. After consulting a few GitHub pages and a very solid YouTube video, I was able to dump eveything, modify the BIOS files and reflash without any issues at all. I went ahead and installed a Dell DW1820a Wireless AC card that I previously had for the T440S hackintosh and had no problems getting both bluetooth and Wifi to work in Windows after installing drivers. 

# The True Cost of a $49 ThinkPad
![please don't judge me based on my love for 2B](https://github.com/tiduscrying/tiduscrying.github.io/raw/main/_images/t440p/PXL_20220112_061511967.jpg)

At this point, I had sank a bit more money into the project than I had originally intended to. Even though I knew going into the project that I would be spending a bit to get replace the missing components, I didn't forsee also having to order a replacement motherboard. 

Breaking down the cost of everything I needed to get it up and running:
- The laptop itself - $69.44
- Replacement 1080p panel - $95.18
- Replacement backlit keyboard - $36.99
- 9 cell battery off Amazon - $43.99
- Replacement BIOS flasher clips & new CMOS battery - $27.26
- 8GB DDR3L stick of RAM - $19.83
- Transcend 250GB M2 SATA 2240 SSD - $50.98
- Not counted - upgraded components (maybe I'll discuss them in the next post)

**Grand Total?:** $343.67

For a 4th gen i5 4200M, 8GB of RAM and a 250GB SSD... Maybe not the _best_ price ever. Truth be told, if I spent a bit more time looking on eBay, I might have been able to find something with less things missing. I most certainly could have found something that posted to the BIOS and at least had a functioning display. But at the end of the day, I had fun doing all of this. Sure, it was money and time spent on something that some may call obsolete, but it's things like this that I _genuinely_ enjoy doing. Laptops don't come like this anymore. You are lucky if you can get a modern laptop with a replaceable SSD, let alone have access to well documented parts lists and easily accessible components. The ThinkPads of yore are testaments to movements such as "Right to Repair" and stand in their own little corner for nerds like me to drool over. 

I did end up upgrading the processor, trying different cooling solutions, adding USB-C charging and turning the T440P into a very usable Hackintosh, but given how long this post already is (and how I tend to ramble), I'll try to make it a new post.

---

If you've stumbled upon this post and managed to stick around until now, thanks for giving it a read. I already have more things I want to talk about once I figure out how to get Jekyll and this blog up and running. Stay tuned in if you're interested!

~ Tiduscrying (02-14-22)
