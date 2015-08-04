## The repo

after many discussions on which is the best approach to reduce cSploit devs efforts, we choose the forked repo solution.
Having a forked repo will allow us to build a package containing all the required gems, without downloading them from a custom server.

### Update from upstream

After cloning the cSploit MSF repo add the official one as follow:

```
git remote add upstream "https://github.com/rapid7/metasploit-framework.git"
```

From now on every time you'll `git fetch` from the upstream remote you'll get the official MSF commits.

TODO: describe merge  [merge or rebase? -ft]

### packaging

put native gems into `/vendor` folder and zip the whole repo.

TODO: explain how to cross-compile gems.

### deploy

just create a new release and add the freshly built package as an attachment.
a release will be used by cSploit only if it has the `csploit` inside the pre-release part ( see [semantic versioning](semver.org) ), like `v1.0.0-csploit`.

the attached package will be downloaded and installed on the device after the user agreement.

## Installation

the installation process is manly composed by 3 parts:

  - extraction
  - patch
  - bundle

### extraction

just a simple extraction of your package into the target MSF directory.

### patch

since every device can have the `env` program installed somewhere around we must change the shebang of every script.

a little example:

```diff
-#!/usr/bin/env ruby
+#!/system/xbin/env ruby

puts "hello world"
```

### bundle

bundler will be installed to get gems required by the MSF.
native gems should be placed into the `/vendor` folder, thus to skip compiling phase.
ensure to match native gems version in bundle specs, thus to use gems from `/vendor`, and not an updated one from rubygems.org .