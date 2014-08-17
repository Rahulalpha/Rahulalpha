## Introduction
this page will help you using the MetaSploit Framework ( MSF ) in dSploit.

## installation
go in `Settings > MetaSploit Framework` and ensure to have both MSF and updates enabled. a dialog will ask you to update Ruby, answer yes. after that another dialog will ask you to update the MSF, answer yes. 

__*done*__.

the process it's quite long, so please wait. you can close dSploit and use your phone for any other purpose during the installation.

### install on sdcard
if your phone does not have much space on it's internal filesystem you can use an external sdcard for store the MSF, change the MSF and Ruby directory under `Settings > MetaSploit Framework` to a directory on your sdcard ( like `/sdcard/msf` and `/sdcard/ruby` ).

### install on old phones ( low RAM )
i've experienced many OutOfMemory ( OOM ) during my installation tests on a phone with only 300MB of RAM. solution is to start the installation and close dSploit.

### trouble shooting
if something goes bad during the installation process go in `Settings > MetaSploit Framework` and click on `Delete MSF`, then restart dSploit. if the problem keep occurring please open a new issue on github.

## using the MSF
after you found an open port with the port scanner ( or the Inspector ) run the Vulnerability Finder to search for known vulnerabilities. after that run Exploit Finder to search for usable MSF Exploits. now, alway from the Exploit Finder, you can customize the exploit options, choose a specific target, change the used payload and launch it by long-pressing on a found exploit. if the launched exploit has succeeded open Sessions to see what session are open on the victim. from here you can do a lot of things but currently only a few works: use a shell or clear logs.

that's all folks.

will update this article with some screenshot if it's necessary.