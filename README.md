<p align="center">
  <img src="https://raw.githubusercontent.com/slatedocs/img/main/logo-slate.png" alt="Slate: API Documentation Generator" width="226">
  <br>
</p>

## Deploying [docs.polkaholic.io](https://docs.polkaholic.io):
```
# use "pushslate"
alias pushslate='cd /root/go/src/github.com/wolkdb/slate; ./deploy.sh;'
root@moonriver:~/go/src/github.com/wolkdb/slate# pushslate
== Sprockets will render css with ruby sass
   consider using Sprockets 4.x to render with SassC
   identical  build/stylesheets/print-953e3353.css
   identical  build/stylesheets/screen-86b5af50.css
   identical  build/images/logo-8f5bad54.png
   identical  build/images/navbar-cad8cdcb.png
   identical  build/fonts/slate.woff
   identical  build/fonts/slate.woff2
   identical  build/fonts/slate-7b7da4fe.ttf
   identical  build/fonts/slate-cfc9d06b.eot
   identical  build/fonts/slate-e55b8307.svg
      create  build/CNAME
   identical  build/javascripts/all_nosearch-18c3ed8e.js
   identical  build/javascripts/all-b12a2749.js
   identical  build/index.html
Project built successfully.
Warning: Permanently added 'github.com,140.82.112.3' (ECDSA) to the list of known hosts.
09540291e1de74d993b059517b0b52a48591a2f1	refs/heads/gh-pages
Warning: Permanently added 'github.com,140.82.112.3' (ECDSA) to the list of known hosts.
remote: Enumerating objects: 2, done.
remote: Counting objects: 100% (2/2), done.
remote: Total 2 (delta 1), reused 2 (delta 1), pack-reused 0
Unpacking objects: 100% (2/2), done.
From github.com:colorfulnotion/slate
   7e8d826..0954029  gh-pages   -> gh-pages
   94029a1..0954029  gh-pages   -> origin/gh-pages
[gh-pages 644a06c] publish: Merge pull request #4 from colorfulnotion/docTest2
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 .nojekyll
Warning: Permanently added 'github.com,140.82.112.3' (ECDSA) to the list of known hosts.
```
Make sure CNAME file is set in source folder.
```
# check CNAME file
root@moonriver:~/go/src/github.com/wolkdb/slate# cat source/CNAME;
docs.polkaholic.io
```

*Instead of putting the `CNAME` file in the root directory of your Slate, you should put it in the `source` folder. When Middleman publishes to the gh-pages branch, it will copy it to the root folder of that branch.

## Prototyping [moonriver.paraholic.io:4567](http://moonriver.paraholic.io:4567):
```
# use "bb"
alias bb='cd /root/go/src/github.com/wolkdb/slate; bundle exec middleman server'
root@moonriver:~/go/src/github.com/wolkdb/slate# bb
== The Middleman is loading
== Sprockets will render css with ruby sass
   consider using Sprockets 4.x to render with SassC
== View your site at "http://moonriver.local:4567", "http://10.128.0.45:4567"
== Inspect your site configuration at "http://moonriver.local:4567/__middleman", "http://10.128.0.45:4567/__middleman"
```
## Dependencies

Minimally, you will need the following:

* [Ruby](https://www.ruby-lang.org/en/) >= 2.5
* [Bundler](https://bundler.io/)
* [NodeJS](https://nodejs.org/en/)
* [Git](https://git-scm.com/)

Please note, only Linux and macOS are officially supported at this time. While slate should work on Windows, it is unsupported.

See below for installation instructions for different OSes / distros.

### Installing Dependencies on Linux

Install Ruby, NodeJS, and tools for compiling native ruby gems:

**On Ubuntu 18.04+**

```bash
sudo apt install ruby ruby-dev build-essential libffi-dev zlib1g-dev liblzma-dev nodejs patch
```

**On Fedora 31+**

```bash
sudo dnf install @development-tools redhat-rpm-config ruby ruby-devel libffi-devel zlib-devel xz-devel patch nodejs
```


Then, update RubyGems and install bundler:

```bash
sudo gem update --system
sudo gem install bundler
```
**Note*

If you get the following error

`ERROR: Your RubyGems was installed trough APT, and upgrading it through RubyGems itself is unsupported.`

try the following commands instead:
```bash
sudo apt-get update -y
sudo apt-get install -y bundler
```


### Installing Dependencies on macOS

First, install [homebrew](https://brew.sh/), then install xcode command line tools:

```bash
xcode-select --install
```

Agree to the Xcode license:

```bash
sudo xcodebuild -license
```

Install nodejs runtime:

```bash
brew install node
```

Update RubyGems and install bundler:

```bash
gem update --system
gem install bundler
```

## Getting Set Up

1. Fork this repository on Github.
2. Clone *your forked repository* (not our original one) to your hard drive with `git clone https://github.com/YOURUSERNAME/slate.git`
3. `cd slate`
4. Install ruby gems for slate:

```shell
# either run this to run locally
bundle install
```

Note: if the above fails on installing nokogiri and using macOS see
[here](https://github.com/sparklemotion/nokogiri.org/blob/master/docs/tutorials/installing_nokogiri.md#macos)
for some helpful tips on things that might help.

## Running slate

You can run slate in two ways, either as a server process for development, or just build html files.

To do the first option, run:

```bash
bundle exec middleman server
```

and you should see your docs at http://localhost:4567. Whoa! That was fast!

The second option (building html files), run:

```bash
bundle exec middleman build
```

## What Now?

The next step is to [learn how to edit `source/index.md` to change the content of your docs](Markdown-Syntax). Once you're done, you might want to think about [deploying your docs](https://github.com/slatedocs/slate/wiki/Deploying-Slate).
