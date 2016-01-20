Laptop
======

Laptop is a script to set up an OS X computer for web development.

It can be run multiple times on the same machine safely. It installs,
upgrades, or skips packages based on what is already installed on the machine.

This particular version of the script is geared toward beginners who want to
set up a Ruby on Rails environment on their Mac. More advanced users can
easily [customize](#customize-in-laptoplocal) the script to install additional
tools. To see an example of a more advanced script, check out
[18F/laptop](https://github.com/18F/laptop).

Requirements
------------

I support clean installations of these operating systems:

* [OS X Yosemite (10.10)](https://www.apple.com/osx/)
* OS X Mavericks (10.9)

Older versions may work but aren't regularly tested. Bug reports for older
versions are welcome.

Install
-------

Begin by opening the Terminal application on your Mac. The easiest way to open
an application in OS X is to search for it via [Spotlight]. The default
keyboard shortcut for invoking Spotlight is `command-Space`. Once Spotlight
is up, just start typing the first few letters of the app you are looking for,
and once it appears, press `return` to launch it.

In your Terminal window, copy and paste each of these two commands one at a
time, then press `return` after each one to download and execute the
script, respectively:

```sh
git clone https://github.com/associatedpress/laptop.git
bash laptop/mac 2>&1 | tee ~/laptop.log && source ~/.rvm/scripts/rvm
```

The [script](https://github.com/associatedpress/laptop/blob/master/mac) itself is
available in this repo for you to review if you want to see what it does
and how it works.

Note that the script will ask you to enter your OS X password at various
points. This is the same password that you use to log in to your Mac.

Once the script is done, quit and relaunch Terminal.

[Spotlight]: https://support.apple.com/en-us/HT204014

What it sets up
---------------

* [Bundler] for managing Ruby gems
* [Flux] for adjusting your Mac's display color so you can sleep better
* [GitHub for Mac] for setting up your SSH keys automatically
* [Heroku Toolbelt] for deploying and managing Heroku apps
* [Homebrew] for managing operating system libraries
* [Homebrew Cask] for quickly installing Mac apps from the command line
* [Homebrew Services] so you can easily stop, start, and restart services
* [hub] for interacting with the GitHub API
* [PhantomJS] for headless website testing (unless on El Capitan, due to
[this bug](https://github.com/Homebrew/homebrew/issues/42249))
* [Postgres] for storing relational data
* [RVM] for managing Ruby versions (includes the latest [Ruby])
* [Sublime Text 3] for coding all the things
* [R]
* [RStudio]
* [Slack]
* [Tabula]
* [PGAdmin3]
* [Open Refine]
* [Python]
* [pip]
* [CSVKit]
* [Agate]
* [ruby 1.8.7-p334]
* [ruby 1.9.3-p448] Sets this as your default ruby in rvm
* [JAVA 6 for OS X 10.10] Patch that allows newer versions of OS X to run apps requiring JAVA 6.
* [PhantomJS] Headless wesite testing. (not yet working on El Capitan).
* [bundler]
* [Flux] Allows you to adjust your Mac's display color

[Bundler]: http://bundler.io/
[Flux]: https://justgetflux.com/
[GitHub for Mac]: https://mac.github.com/
[Heroku Toolbelt]: https://toolbelt.heroku.com/
[Homebrew]: http://brew.sh/
[Homebrew Cask]: http://caskroom.io/
[Homebrew Services]: https://github.com/gapple/homebrew-services
[hub]: https://github.com/github/hub
[PhantomJS]: http://phantomjs.org/
[Postgres]: http://www.postgresql.org/
[Ruby]: https://www.ruby-lang.org/en/
[RVM]: https://github.com/wayneeseguin/rvm
[Sublime Text 3]: http://www.sublimetext.com/3
[R]: https://www.r-project.org/
[RStudio]: https://www.rstudio.com/
[Slack]: https://slack.com/
[Tabula]: https://github.com/tabulapdf/tabula
[PGAdmin3]: http://www.pgadmin.org/
[Open Refine]: https://github.com/OpenRefine
[Python]: https://www.python.org/
[pip]: https://pypi.python.org/pypi/pip
[CSVKit]: https://csvkit.readthedocs.org/en/0.9.1/
[Agate]: http://agate.readthedocs.org/en/1.1.0/install.html
[JAVA 6 for OS X 10.10]: https://support.apple.com/kb/dl1572?locale=en_US
[PhantomJS]: http://phantomjs.org/
[bundler]: http://bundler.io/
[Flux]: https://justgetflux.com/




It should take less than 40 minutes to install (depends on your machine and
internet connection).


Customize in `~/.laptop.local`
------------------------------
```sh
# Go to your OS X user's root directory
cd ~

# Download the sample file to your computer
curl --remote-name https://raw.githubusercontent.com/monfresh/laptop/master/.laptop.local

# open the file in Sublime Text
subl .laptop.local
```

Your `~/.laptop.local` is run at the end of the `mac` script.
Put your customizations there. You can use the `.laptop.local` you downloaded
above to get started. It lets you install the following tools
(commented out by default):

* [Atom] - GitHub's open source text editor
* [CloudApp] for sharing screenshots and making an animated GIF from a video
* [Firefox] for testing your Rails app on a browser other than Chrome or Safari
* [iTerm2] - an awesome replacement for the OS X Terminal

[Atom]: https://atom.io/
[CloudApp]: http://getcloudapp.com/
[Firefox]: https://www.mozilla.org/en-US/firefox/new/
[iTerm2]: http://iterm2.com/

To install any of the above tools, uncomment them from `.laptop.local` by
removing the `#`. For example, to install CloudApp, your `.laptop.local`
should look like this:

```sh
#!/bin/sh

# brew_cask_install 'atom'
brew_cask_install 'cloud'
# brew_cask_install 'firefox'
# brew_cask_install 'iterm2'
```

Write your customizations such that they can be run safely more than once.
See the `mac` script for examples.

Laptop functions such as `fancy_echo`, `brew_install_or_upgrade`,
`gem_install_or_update`, and `brew_cask_install` can be used in your
`~/.laptop.local`.

Debugging
---------

Your last Laptop run will be saved to a file called `laptop.log` in your home
folder. Read through it to see if you can debug the issue yourself. If not,
copy the lines where the script failed into a
[new GitHub Issue](https://github.com/monfresh/laptop/issues/new) for me.
Or, attach the whole log file as an attachment.

Credits
-------

This laptop script is forked from
[Moncef Belyamani's laptop](https://github.com/monfresh/laptop) script, which
in turn was inspired by 
[thoughbot's laptop](https://github.com/thoughtbot/laptop) script.

### Public domain

thoughtbot's original work remains covered under an [MIT License](https://github.com/thoughtbot/laptop/blob/c997c4fb5a986b22d6c53214d8f219600a4561ee/LICENSE).

My work on this project is in the worldwide [public domain](LICENSE.md), as are contributions to my project. As stated in [CONTRIBUTING](CONTRIBUTING.md):

> This project is in the public domain within the United States, and copyright and related rights in the work worldwide are waived through the [CC0 1.0 Universal public domain dedication](https://creativecommons.org/publicdomain/zero/1.0/).
>
> All contributions to this project will be released under the CC0 dedication. By submitting a pull request, you are agreeing to comply with this waiver of copyright interest.
