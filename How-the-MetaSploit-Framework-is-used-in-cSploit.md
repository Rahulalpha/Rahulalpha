## introduction
cSploit has a cool MetaSploit Framework ( MSF ) integration feature, which use it to launch exploits and control infected machines.

This features has been introduced by [tux_mind](https://github.com/tux-mind) on autumn of 2013. the first version used a Gentoo armv7a image with ruby 2,0 and MetaSploit Framework 4.4, it was about 800MB large.

In spring 2014 we used another approach, we ported ruby to android and use ruby and the MSF directly over the android libc, shrinking the size to about 150MB :blush:

The MetaSpoit Framework it's a collection of ruby scripts that simplify and automate the pwning process.
it's entirely written in ruby and require some extra gems to work properly.

## Ruby
### The interpreter
the ruby interpreter has been ported on the bionic libc to run over android devices, using the android NDK and editing a little the ruby sources. our ruby repo it's [here](https://github.com/tux-mind/ruby/tree/ruby_1_9_3) if you want see our modifications.

### Rubygems
rubygems it's the gem that manage all the others. unfortunately the rubygems shipped with ruby 1.9.3 it's quite old and lacks some SSL certificates required to fetch additional gems.

thus we have to update it in the ruby update process.

### Gems
MSF use a lot of gems, and many of them must be compiled from C sources, but Android does not comes with a compiler, so we have to compile them with our developer tools. those gems are not trivial to compile for android , it took a lot of work.

We created a gem server that host compiled gems, thus to make the installation process download them pre-compiled, no compiler needed.

## The MetaSploit Framework RPCD
MSF has a cool program called `msfrpcd`, that program will provide access to a MSF instance thought a RPC connection. cSploit start the RPC daemon and connect to him.

After that cSploit it's ready to launch exploits and control opened sessions on pwned targets.

On an opened session you can take control of a shell, clear event logs and many more. the target it's yours :wink:

## Missing features
Currently there are many features of the MSF that cSploit does not use.
we want to take advantage of all the MSF features.
these are features that are currently missing but are in our roadmap:

  - use auxiliary modules
  - hack printers
  - open VNC connections

Any other missing features can be requested using our [issue tracker](https://github.com/cSploit/android/issues).