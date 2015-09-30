**DRAFT:  This tutorial is a work-in-progress.  Please read with a grain of salt as it needs peer-review, commentary, corrections, and changes.**

### Introduction

It is critical to use encrypted, authenticated connections for all network traffic.  However, many web sites and apps today continue to transfer data "in the clear" without encryption and without authenticating the origin and integrity of messages passed through the network.

This is really dumb.

cSploit has many neat functions, one of which is to perform so-called "[Man-In-The-Middle](https://en.wikipedia.org/wiki/Man-in-the-middle_attack)" (MITM) attacks, which can be useful for demonstrating in a dramatic fashion exactly why this is dumb, how data can be harvested and manipulated by a third party, and the critical importance to properly encrypt network communications.

Essentially, a MITM attack involves cSploit inserting itself "between" two or more parties on the network, intercepting, collecting, and even altering communications as they are passed back and forth.

While cSploit allows for many types of MITM attacks, this tutorial will focus on two simple built-in demonstrations that are easy for the layperson to appreciate. 

Before we begin, an important note:

*Note: It's critical to mention/insist that cSploit is intended to be used for legal security purposes only, and you should only use it to protect networks/hosts you own or have permission to test. Please don't be an asshole, and be sure that you understand and are complying with the cSploit licenses and laws in your area.*

It is also important to observe that the MITM demonstration may disrupt and compromise the integrity of normal network operation for others in the network, so do not use it if important work is going on (and again don't use it without appropriate permission).

### Part One:  Choose your target

When you first launch cSploit, and after it has downloaded any required updates, you will be presented with discovered items on your network. These may include routers, computers, phones, tablets, printers, and more.

<img src="http://i.imgur.com/cFll5P9.jpg" width="250">

In the image above, you'll notice a globe icon with `192.168.0/24` after it, which in many local networks refers to the entire local network (ie, relates to ALL the local hosts).

While you can select a single item from this list, for dramatic purposes, we'll assume you want to MITM attack the *entire* network.  So, select the referenced item labeled "**This is your network subnet mask**" to attack all devices on the local network.

You'll now should see an item called **MITM**.  Select that to proceed to the Man-In-The-Middle attack menu.

### Part Two:  Replace text on your local network's Web connections

To get an idea of what a MITM can do, visit a web site that does not use encryption.  At the time this tutorial was written, the web site of the [New York Times](http://nytimes.com) is not using SSL-- secure socket layers-- to encrypt and authenticate its content or origin.  That is, the web site begins with `http` rather than `https`.

***Lengthy Caveat:  Just because a web site address starts with `https://` does not necessarily mean you are 100% secure!  For one thing, some web sites may include links from _within_ the secure page to non-encrypted content, such as: `<img src="http://someaddress.example.com/notencrypted.jpg"/>`.  (When this occurs, this is often mentioned in the browser if you click on the "lock" icon.)  There are also ways to "strip" the SSL off the web site as part of a MITM attack (hoping the user won't notice the lack of a "lock" type icon)... as well as other methods that may be used to create the illusion of a secure connection even when the lock is in place.  (compromised certificates, etc.)   Additionally, a computer may have been attacked in ways that does not involve the security of the SSL connection itself-- keyboard loggers, screen captures, etc. to give access to a web page's information even when the page itself in the browser was delivered securely.  All this said, while SSL does not create perfect security, it's probably safe to say it is FAR wiser to use it than not to do so.***

[IMAGE HERE]

Back to the New York Times.  Say the headline currently says:  **CURRENT HEADLINE IN SCREENSHOT** and you want to change it to **cSploit Voted Best Android App** for everyone in your local network (and with emphasis again, you must have all appropriate permissions to do something like this!)

Select the item called **Custom Filter**, and in the **From** column, type "**CURRENT HEADLINE**".  Be sure to get the capitalization and spacing correct.  Then, in the **To** column to its right type "cSploit Voted Best Android App".  Then press **OK**.

You should see a spinning progress icon over the **Custom Filter** item.  If all goes right, within a few moments, anyone visiting nytimes.com on the local network should see the new headline has replaced the original:

[IMAGE HERE]

To turn off the MITM, simply re-press the icon.

### Part Three:  Replace images on your local network's Web connections

The goal here is to, just as you replaced text previously, to _replace images loaded by other computers while visiting insecure websites with substitute images of your own choosing_.  It can be done with a few taps of your finger.

To try this, select the item called **Replace Images**.  Then choose a source image.  You can use an image file already located on your own device, such as one taken by your camera.  Or you can use the **Web URL** option to redirect to an image stored elsewhere.

*Tip:  You might not want to select an image that's too large-- since these are going on web pages in place of other random images, you want them to be sized appropriately.*

Once you've selected your image, you will return to the previous menu, and a progress icon will appear, indicating that the MITM replacement attack is ongoing.  To halt the MITM, just tap the icon again and things should return to normal.

While the attack is underway, if you load an non-encrypted web site on any web browser in your local network (one starting with `http://` rather than `https://`), you will hopefully now notice your image appearing on the page in place of existing ones.

The pages may load slower than usual as your phone is now intercepting and replacing the content.  And some images will not be affected at all.

Again, to stop the attack, choose the **Replace Images** option.

### Part Four:  Additional MITM possibilities....

You'll find other items in cSploit which work similarly by replacing videos or inserting javascript "Alerts" to demonstrate that a page has been modified.

Another item, **Simple Sniff**, offers the ability to log network activity to a `pcap` file.  This may be useful for debugging network issues, among other purposes.

Another feature of note is the ability to observe unencrypted [http cookies](https://en.wikipedia.org/wiki/HTTP_cookie), including cookies used to identify "sessions" (that is, cookies which are used to maintain continuity for a user between multiple visits to a web site).  The **Session Hijacker** feature can then be used to transfer that session to cSploit and continue the session locally.

###  Conclusion

Hopefully the above features really make the point-- the era of cleartext, unencrypted network connections are over.  It is critical to use SSL or other peer-tested public encryption measures for communication everywhere, whether for HTTP connections, online chats, checking email, etc.

See also:

* [SSL Everywhere](https://www.eff.org/https-everywhere%20) -- a free browser plugin from the [Electronic Freedom Foundation](http://www.eff.org) that makes it easier to use SSL everywhere
* [HTTPS Everywhere](https://www.youtube.com/watch?v=cBhZ6S0PFCY) -- a video from Google discussing the critical importance of using secure connections everywhere.