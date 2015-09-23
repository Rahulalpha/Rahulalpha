## Introduction
This page will help you using the MetaSploit Framework ( MSF ) in cSploit.

## Installation
On first app launch dialog will ask you to update Ruby, answer yes.
After that another dialog will ask you to update the MSF, answer yes.

__*done*__.

The process it's quite long, so please wait, you can close cSploit and use your phone for any other purpose during the installation.

### Install on SDCard
if your phone does not have much space on it's internal filesystem you can use an external sdcard for store the MSF, change the MSF and Ruby directory under `Settings > MetaSploit Framework` to a directory on your sdcard ( like `/sdcard/msf` and `/sdcard/ruby` ).

## Troubleshooting

### Install on old phones ( low RAM )
I've experienced many OutOfMemory ( OOM ) during my installation tests on a phone with only 300MB of RAM. solution is to start the installation and close cSploit.

### Restart from clean
If something goes bad during the installation process go in `Settings > MetaSploit Framework` and click on `Delete MSF`, then restart cSploit. if the problem keep occurring please open a new issue on github.

## Using the MSF

  1. Find services running using the `Inspector`
     ![Inspector](http://s28.postimg.org/noigvl92l/Screenshot_2015_09_23_23_48_43.png)

  2. Find exploits for those vulnerabilities using the `Exploit Finder`
     ![Exploit Finder](http://s10.postimg.org/gsszn502x/Screenshot_2015_09_23_23_49_33.png)

  3. customize exploits by playing with their options if you need.

  5. launch the exploit

  6. Use opened session on pwned targets using the `sessions` plugin

That's all for now folks.

Will update this article with some screenshot if it's necessary.

## Footnote

Please read carefully each exploit full description before using them. This app is intended to use on network with the agreement of the sysadmin. You can cause high damages to vulnerable machines, thus be careful.

cSploit it's an handy app for security experts, not a toy that magically gives you control of every computer.