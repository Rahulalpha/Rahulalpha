## Introduction
cSploit integrates the [MetaSploit Framework](http://www.metasploit.com) (often abbreviated to msfw), an open-source computer security suite of Ruby scripts that simplifies the identification of potential security holes and automate the exploitation process via built-in *modules*.  msfw can be used to launch exploits and subsequently administrate exploited hosts via command and control *sessions*.

The framework is entirely written in ruby and require some extra gems to work properly.

This msfw integration with cSploit was first introduced by [tux_mind](https://github.com/tux-mind) in autumn of 2013.  The first implementation used a Gentoo armv7a image with ruby 2.0 and MetaSploit Framework 4.4 and was about 800MB in size.

In spring 2014, we used another approach:  We ported Ruby and the MSF directly over to use the native Android version of the standard C library, called [bionic](https://en.wikipedia.org/wiki/Bionic_(software)), shrinking the size to about 150MB in the process. :blush:


## Ruby
### The interpreter
As mentioned above, The Ruby interpreter has been ported to run over android device and is built with the standard android NDK.   Our ruby repository with the required modifications is [here](https://github.com/tux-mind/ruby/tree/ruby_1_9_3).

### Rubygems
This is the gem that manages all the others.  Unfortunately the rubygems shipped with ruby 1.9.3 is quite old and lacks some SSL certificates required to fetch additional gems.

Thus we will have to update it in the ruby update process.  Stay tuned.

### Gems
MSF uses a good number of gems, and many of them must be compiled from C sources.  But Android does not comes with a built-in compiler, so we opted to compile them with our developer tools in advance, then download them from the app.

Those gems are not trivial to compile for Android-- it took a lot of work.  The result was a bundle of compiled gems that are delivered to the app via a gem server.  This makes the installation process a lot simpler, and allows us to update the gems as needed without requiring a compiler on Android itself.

## The MetaSploit Framework RPCD
MSF has a cool program called `msfrpcd`.  This program provides access to a MSF instance through a RPC (remote procedure call) connection.

cSploit starts the RPC daemon and connect to it.  After that, cSploit can make MSF launch exploits and control sessions on compromised targets.

Once a target host has been compromised, you can take control of a shell, clear event logs, etc. the target is yours :wink:

## Missing features
MSF is a very sophisticated product, and there are many features of the MSF that cSploit currently does not use.  Eventually, we want to take advantage of all the MSF features.

These are features that are currently missing but are in our roadmap:

  - use auxiliary modules
  - hack printers
  - open VNC connections

Any other missing features can be requested using our [issue tracker](https://github.com/cSploit/android/issues).