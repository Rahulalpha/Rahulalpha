### Introduction

In this quick tutorial, you'll learn how to test the hosts (in this case, a deliberately vulnerable "virtual computer") on your network for potential security weaknesses using cSploit.  That means scanning the network, picking a host, scanning it for services and potential vulnerabilities, launching an exploit, and connecting to a root session.

It's done in five basic steps.  All from your Android device.

*Note:  It's critical to mention/insist that cSploit is intended to be used for legal security purposes only, and you should only use it to protect networks/hosts you own or have permission to test.  Please don't be an asshole, and be sure that you are complying with the cSploit licenses and laws in your area.*

Okay, that said, let's get started.

### Step One:  Set up a vulnerable computer on your network for testing.

Yes, you are going to install a "machine" (okay, a virtual machine, or "VM") with known security holes to practice on.  For our tutorial, let's take a look at the [Metasploitable2 virtual machine](http://sourceforge.net/projects/metasploitable/files/Metasploitable2/), a deliberately vulnerable linux VM made way back in 2012.  As the description notes:

> Metasploitable is an intentionally vulnerable Linux virtual machine. This VM can be used to conduct security training, test security tools, and practice common penetration testing techniques. 

You can read more about Metasploitable at Rapid7's site [here](https://community.rapid7.com/docs/DOC-1875) and download (a more recent version?) from them [here](https://information.rapid7.com/metasploitable-download.html).

You can use something like [VirtualBox](https://www.virtualbox.org/wiki/Downloads) to run Metasploitable.  There is documentation available elsewhere on setting this up, as the instructions will vary depending on the operating system of your PC.

The goal though is to have it running so it appears as a host on your local network.  A simulation of a vulnerable machine that you will use to test cSploit's functionality.
 
### Step Two:  Start cSploit and scan the local network

Make sure your phone/tablet with cSploit is connected on the same local network as the Metasploitable2 virtual machine you just installed.

When you launch cSploit, and after it has downloaded any required updates, you will be presented with discovered items on your network.  These may include routers, computers, phones, tablets, printers, and more.  You may also see a globe icon with your network and a "/24" after it, which in many local networks refers to the entire network (ie, relates to ALL the local hosts).

You can press the **+** button to add your own hosts, which do not have to be in your local network.  (Again, do not add any hosts that you do not have explicit permission to test.)

If all goes well, you'll see an item called "METASPLOITABLE" in the list.  If you select it, you can continue to...

### Step Three:  Scan for services with Service Inspector

Now you're greeted with a list of options pertaining to this host, METASPLOITABLE.  You can do a lot of things here, but we're going to focus on the Service Inspector, which uses a scanner called [nmap](https://en.wikipedia.org/wiki/Nmap) to probe the METASPLOITABLE virtual machine to see what services are available.

So if you press the **Start** button and wait a few moments, you'll get a list of discovered potential services that appear to have been "turned on" on the METASPLOITABLE host, along with their associated port numbers.

Once you have the list, you can hit the back button and we'll search for exploits for those services...

### Step Four:  Use the Exploit Finder to search for potential security holes

Now go to the **Exploit Finder** and again, press **Start**.  You will see a list of "exploits", which are special instructions designed to penetrate a known vulnerability in the service that was scanned in the previous step.

To "launch" the exploits, the cSploit app uses a system called the **[Metasploit framework](https://www.metasploit.com/)**, sometimes abbreviated to **msf** or **msfw**, behind the scenes.  When cSploit first starts, the "Metasploit Remote Procedure Call Daemon (RPCD)" needs to start running, and cSploit will connect to it.  This happens automatically, but can take a while-- a few minutes sometimes-- and cSploit lets you do other things while it's connecting.

You want to be sure that it's connected before you try to launch an exploit.  Check if Metasploit's RPCD is connected by looking at the notification (ie, the pulldown screen) area at the top of Android.  It gets updated as the connection status changes, so once it's green and says "Connected to Metasploit", you should be good to go.

But back to the exploit list-- many of these exploits won't work for one reason or another-- maybe they are old or patched now or depend on specific conditions that aren't quite available-- but for the METASPLOITABLE2 package in our example, there should be one called **[exploit/unix/ftp/vsftpd_234_backdoor](http://www.rapid7.com/db/modules/exploit/unix/ftp/vsftpd_234_backdoor)** that can do the trick.  If you select it, then choose **Launch**, you should see a message **Job started**.

### Step Five:  Claim your root shell!

Now hit the back button again to go back to the METASPLOITABLE-related options.  Under the **Sessions** button, you should see a new entry:  **Command shell**

Press that, and you should hopefully be given a console screen.  If you type `whoami` you should be told that you are in the `root` account!  And you can remove files, create users, etc.

If this was a real system and not a test VM, your machine would be owned!  This would be a pretty persuasive sign that it's past time to update your FTP server on that machine.