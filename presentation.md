class: center, middle

background-image: url(images/crowd.jpg)

![Ents24 Logo](images/logo.png)

# Tips & Tricks



---
class: center, middle
#PHP Tools & Libraries

---
##Debug Console

* Run code snippets
* Create minimal test cases
* Code stored in session - still there if you refresh the page or close the tab
* `github.com/Seldaek/php-console`

![](images/debug1.png)

---
##Debug Console

* Set a bootstrap file that points to your autoloader to have full access to your codebase
* Create a Dependency Container, grab services and prototype code

```php
<?php

$defaults = array(
    // how many spaces to use for indention, 0 will make it use real tabs
    'tabsize' => 0,

    // whitelist of IPs which don't need to be authenticated
    // use '*' to allow any IP
    'ip_whitelist' => array('127.0.0.1', '::1', '10.0.2.2'),

    // bootstrap file, if defined this file will be included before
    // the code entered by the user is evaluated. any variables and classes
    // defined here will be accessible by the eval'd code
    'bootstrap' => "global.php",
);
```

---
##Kint

* `var_dump` / `print_r()` replacement for debugging
* `raveren.github.io/kint/`

![](images/kint1.png)

---
##Kint
* Prints strings, JSON, arrays, objects
* Has both HTML and text-only output
* `d` = debug, `dd` = debug and die

![](images/kint2.png)

---
##Kint
* `debug_backtrace()` replacement - browse the call stack and all arguments passed along the way

![](images/kint3.png)

---
##Amiss
* Data mapper ORM
* Keeps its hands off your codebase - POPO
* Works well as part of a Repository pattern, lets you keep all persistence logic away from business logiv

.center[
![](images/amiss1.png)
]

---
##Amiss
* Fantastic documentation - narrative and comprehensive
* Comprehensively unit tested

.center.w70[
![](images/amiss2.png)
]

---
##XDebug & Webgrind
* Helps you find out where code is spending its time
* XDebug extension generates profile information
* Webgrind makes the profile information browsable and understandable
* Configurable using extensions for Firefox & Chrome:

![](images/xdebug-firefox.png)
![](images/xdebug-chrome.png)

* Click the button, reload the page

---
![](images/webgrind1.png)

---
##XDebug & Webgrind

* `xdebug.org/docs/profiler`
* `github.com/jokkedk/webgrind`


* What about CLI scripts?

```
php -d xdebug.profiler_enable=On [script.php]
```

```
alias php-profile="php -d xdebug.profiler_enable=1"
```

---
class: center, middle
#Windows

---
##ConEmu

.center[
![](images/cmd1.png)
]

---
##ConEmu

.center[
![](images/conemu1.png)
]

---
##ConEmu

.center[
![](images/conemu2.png)
]

---
##ConEmu

* `conemu.github.io`


* Great for hosting Powershell & Cmd.exe shells

    * Powershell provides aliases for common Linux command line tools - `ls` being the most helpful

* Can split into tiled windows

* Shortucts for common shell configurations - home directories / ssh sessions

* Can host some GUI applications - notepad / file explorer


---
##KiTTy

* Drop in replacement for PuTTY, everyone's favourite windows SSH client

* Adds:
    * Automatic re-connect after suspend / wakeup
    * Resizable config window
    * Folders & filters for managing large lists of hosts
    * Run local scripts & commands on servers with a keyboard shortcut

* `www.9bis.net/kitty/`

---
##Coloured SSH Terminals

* Change the background and text colour of your terminals to make it easy to know where you are

.center[
![](images/terms.png)
]

---
##Coloured SSH Terminals

* In PuTTY / KiTTY:

.center.w70[
![](images/col1.png)
]


---
class: center, middle
#Git

---
##Prompt

* GitHub Desktop gies you a complete, up to date git setup with auto-updating and common linux tools
* Installs PoshGit into Powershell, giving you tab completion and a better prompt

.w80[
![](images/poshgit1.png)
]

* Add this to your Powershell profile to get git everywhere:

```powershell
#Load github shell
. (Resolve-Path "$env:LOCALAPPDATA\GitHub\shell.ps1")
. (Resolve-Path "$env:github_posh_git\profile.example.ps1")
```

* Loads of options for Bash users:
* `github.com/magicmonty/bash-git-prompt`

---
##Aliases

```
  diff2    = diff -b --color-words --diff-algorithm=histogram
  share    = "!git push -u origin \"$(git rev-parse --abbrev-ref HEAD)\""
  nuke     = !sh -c 'git branch -D $1 && git branch -d -r origin/$1 && git push origin :$1' -
```

`git config --global help.autocorrect=1`

```
tips-and-tricks [gh-pages]> git stts

WARNING: You called a Git command named 'stts', which does not exist.
Continuing under the assumption that you meant 'status'
in 0.1 seconds automatically...

On branch gh-pages
Your branch is up-to-date with 'origin/gh-pages'.
Changes not staged for commit:

        modified:   presentation.md

no changes added to commit (use "git add" and/or "git commit -a")
```

---
##Shortcuts

* Instead of `git checkout [FILE]` use `git checkout -- [FILE]`
* `checkout --` gives you tab completion of files you have changed in Git Bash / PoshGit

* &dash; means "last branch"

```
git checkout master
git pull
git checkout mybranch
git rebase master
git checkout master
git merge mybranch
```

```
git checkout master
git pull
git checkout -
git rebase -
git checkout -
git merge -
```

---
class: center, middle

#Questions?