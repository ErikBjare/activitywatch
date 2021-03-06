ActivityWatch
=============


[![Build Status Travis](https://travis-ci.org/ActivityWatch/activitywatch.svg?branch=master)](https://travis-ci.org/ActivityWatch/activitywatch)
[![Build Status Appveyor](https://ci.appveyor.com/api/projects/status/vm7g9sdfi2vgix6n?svg=true)](https://ci.appveyor.com/project/ErikBjare/activitywatch)
[![CII Best Practices](https://bestpractices.coreinfrastructure.org/projects/873/badge)](https://bestpractices.coreinfrastructure.org/projects/873)
[![Documentation](https://readthedocs.org/projects/activitywatch/badge/?version=latest)](http://activitywatch.readthedocs.io)

[Releases](https://github.com/ActivityWatch/activitywatch/releases)
| [Documentation](http://activitywatch.readthedocs.io)
| [Issue tracker](https://github.com/ActivityWatch/activitywatch-user-issues/issues)
| [Website](http://activitywatch.net/)
| [GitHub](https://github.com/ActivityWatch/activitywatch/)
| [Twitter](https://twitter.com/ActivityWatchIt)

ActivityWatch ***records what you do*** so that you can ***become aware of what you do*** and choose to do better. All in a secure way where ***you control the data***.


## About

The goal of ActivityWatch is simple: *Enable the collection of as much valuable lifedata as possible without compromising user privacy.*

We've worked towards this goal by creating a application for safe storage of the data on the users local machine and as well as a set of watchers which record data such as:

 - Currently active application and the title of its window
 - Currently active browser tab and it's title and URL
 - Keyboard and mouse activity, to detect if you are afk or not
</small>
 
It is up to you as user to collect as much as you want, or as little as you want (and we hope some of you will help write watchers so we can collect more).

**Note:** ActivityWatch is under development. There is still work to be done so we provide it with no guarantees with the hope that others may wish to help and give their feedback!

You can read more on our [website](https://activitywatch.github.io/about/).

### Screenshots

<!-- TODO: We could probably stylize these (nice borders, scaled down) -->

<img src="http://activitywatch.net/screenshot.png" width="22%">
<!--
  <img src="http://activitywatch.net/screenshot.png" width="22%">
  <img src="http://activitywatch.net/screenshot.png" width="22%">
  <img src="http://activitywatch.net/screenshot.png" width="22%">
-->

### Is this yet another time tracker?

Yes, but we found that most time trackers lack in one or more important features. 

Common dealbreakers:

 - Open Source
 - Syncronization
 - Ease of use (most others tend to only target programmers)
 - High data resolution (storage of raw data)
 - Plugins (simplicity to collect more data)

We aim to address all of these and we're well on our way, see the table below.

#### Feature comparison


<!-- TODO: Replace Platform names with icons, yes/no with checkbox icons,   -->

|               | User owns data     | GUI                | Sync                     | Open Source        | Platforms                                 |
| ------------- |:------------------:|:------------------:|:------------------------:|:------------------:| ----------------------------------------- |
| ActivityWatch | :white_check_mark: | :white_check_mark: | ~~Decentralized~~ (WIP)  | :white_check_mark: | macOS, Linux, Windows, ~~Android~~ (WIP)  |
| Selfspy       | :white_check_mark: | :x:                | :x:                      | :white_check_mark: | macOS, Linux, Windows                     |
| ulogme        | :white_check_mark: | :white_check_mark: | :x:                      | :white_check_mark: | macOS, Linux                              |
| RescueTime    | :x:                | :white_check_mark: | Centralized              | :x:                | macOS, Linux, Windows, Android, iOS       |
| WakaTime      | :x:                | :white_check_mark: | Centralized              | Client             | Most popular text editors                 |

**Tracking**

|               | Application        | Window Title       | AFK                | Browser Extensions | Editor Plugins           |
| ------------- |:------------------:|:------------------:|:------------------:|:------------------:| ------------------------ |
| ActivityWatch | :white_check_mark: | :white_check_mark: | :white_check_mark: | In Beta            | Possible                 |
| Selfspy       | :white_check_mark: | :white_check_mark: | :white_check_mark:?| :x:                | :white_check_mark:?      |
| ulogme        | :white_check_mark: | :white_check_mark: | :white_check_mark:?| :x:                | :x:?                     |
| RescueTime    | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :x:                      |
| WakaTime      | :x:                | :x:                | :white_check_mark: | :x:                | :white_check_mark:, many |


### Installation & Usage

**We're not there yet for end-users**, however if you are a developer you may try the following:

```sh
# Ensure you have Python 3.5 or later installed
python3 -V

# Now you probably want to set up a virtualenv so we don't install everything system-wide.
sudo pip3 install virtualenv  # Assuming you don't already have it, you might want to use your systems package manager instead.
virtualenv venv --python=python3 --clear
# Now you need to activate the virtualenv
# For bash/zsh users: source ./venv/bin/activate
# For fish users:     source ./venv/bin/activate.fish

# Now we build and install everything into the virtualenv.
make build

# Now you should be able to start ActivityWatch
# Either use the trayicon manager:
aw-qt
# Or run each module seperately:
aw-server
aw-watcher-afk
aw-watcher-window

# Now everything should be running!
# You can see your data at http://localhost:5600/
```

If anything doesn't work, let us know!

## About this repository

This repo is a bundle of the core components and official modules of ActivityWatch (managed with `git submodule`). It's primary use is as a meta-package providing all the components in one repo; enabling easier packaging and installation. It is also where releases of the full suite are published (see [releases](https://github.com/ActivityWatch/activitywatch/releases)).

### Server

`aw-server` is the official implementation of the core service which the other activitywatch services interact with. It provides a datastore and serves the web interface developed in the *aw-webui* project (which provides the frontend part of the webapp).

The webapp includes basic data visualization (WIP), data browsing and export, and has a lot more planned for it.

### Watchers

 - `aw-watcher-afk` - can be used to log the presence/absence of user activity from keyboard and mouse input
 - `aw-watcher-window` - can be used to log the currently active application and it's window title
 - `aw-watcher-web` - (WIP) can be used to increase the logging detail when browsing the web by collecting the URLs and titles of tabs (your web history with superpowers)

### Libraries

 - `aw-core` - core library, provides no runnable modules
 - `aw-client` - client library, useful when writing watchers

## Contributing

We currently don't have much of a good contributors guide (we're working on it), feel free to browse the documentation (also in a early state). You should also send me an email at: [erik@bjareho.lt](mailto:erik@bjareho.lt).
