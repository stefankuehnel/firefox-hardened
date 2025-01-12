# firefox-hardened

[![GitHub Release](../../actions/workflows/github-release.yml/badge.svg)](../../actions/workflows/github-release.yml)

A `user.js` configuration file for Mozilla Firefox designed to harden browser settings and make it more secure.

## ⚙️ Get Started

There are two possible installation variants.

### Single Profile Installation

Copy the [`user.js`](../../releases/latest/download/user.js) file to the Firefox installation directory. The file should be located at:

| OS                         | Path                                                                                                                                                   |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Windows                    | `%APPDATA%\Mozilla\Firefox\Profiles\<GOOGLE_CITYHASH>.your_profile_name\user.js`                                                                       |
| Linux                      | `~/.mozilla/firefox/<GOOGLE_CITYHASH>.your_profile_name/user.js`                                                                                       |
| OS X                       | `~/Library/Application Support/Firefox/Profiles/<GOOGLE_CITYHASH>.your_profile_name`                                                                   |
| Android                    | `/data/data/org.mozilla.firefox/files/mozilla/<GOOGLE_CITYHASH>.your_profile_name`                                                                     |
| Sailfish OS + Alien Dalvik | `/opt/alien/data/data/org.mozilla.firefox/files/mozilla/<GOOGLE_CITYHASH>.your_profile_name`                                                           |
| Windows (portable)         | `[firefox directory]\Data\profile\`                                                                                                                    |

With this installation method, if any of `user.js` settings is changed through [`about:config`](http://kb.mozillazine.org/About:config) or Firefox preferences dialogs, they will be reset to the `user.js` defined values after restarting Firefox. This makes sure they're always back to secure defaults when starting the browser. However this prevents persistently changing settings you don't consider appropriate. Either edit `user.js` directly, or use the system-wide installation method described below.

### System-wide Installation

Download one of the following files:

- [`systemwide_user.js`](../../releases/latest/download/systemwide_user.js): It will be used as a default value for all Firefox Profiles where particular preferences are not explicitly set. It can be changed in `about:config` and is kept across browser sessions.
- [`locked_user.js`](../../releases/latest/download/locked_user.js): It will be used as a default value for all Firefox Profiles where particular preferences are not explicitly set. It cannot be changed in `user.js` or Firefox's `about:config` and is kept across browser sessions. 
- [`debian_locked.js`](../../releases/latest/download/debian_locked.js): Debian specific. Users are not able to override preferences.

Copy the downloaded file to the Firefox installation directory. The file should be located at:

| OS                        | Path                                                                         |
| ------------------------- | ---------------------------------------------------------------------------- |
| Windows                   | `C:\Program Files (x86)\Mozilla Firefox\mozilla.cfg`                         |
| Linux                     | `/etc/firefox/syspref.js`, for older versions: `/etc/firefox/firefox.js`     |
| Linux (Debian)            | `/etc/firefox-esr/firefox-esr.js`                                            |
| Linux (Gentoo, Archlinux) | `/usr/lib/firefox/mozilla.cfg`, might also be `/usr/lib32/` or `/usr/lib64/` |
| OS X                      | `/Applications/Firefox.app/Contents/Resources/mozilla.cfg`                   |

#### Additional installation steps for Windows / OS X / Gentoo / Archlinux

Create a `local-settings.js` in the Firefox installation directory, with the following contents:

```
pref("general.config.obscure_value", 0);
pref("general.config.filename", "mozilla.cfg");
```

This file should be located at:

| OS                        | Path                                                                            |
| ------------------------- | ------------------------------------------------------------------------------- |
| Windows                   | `C:\Program Files (x86)\Mozilla Firefox\defaults\pref\`                         |
| OS X                      | `/Applications/Firefox.app/Contents/Resources/defaults/pref`                    |
| Linux (Gentoo, Archlinux) | `/usr/lib/firefox/defaults/pref/`, might also be `/usr/lib32/` or `/usr/lib64/` |

If `mozilla.cfg` still fails to load, you must add a blank comment to the top of `mozilla.cfg` like so:
```
//
```

## 🐛 Found a Bug?

Thank you for your message! Please fill out a [bug report](../../issues/new?assignees=&labels=&template=bug_report.md&title=).

## 📖 License

This project is licensed under the [MIT License](https://choosealicense.com/licenses/mit/).

```
The MIT License (MIT)

Copyright (c) 2025 Stefan Kühnel
Copyright (c) 2016 pyllyukko

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the “Software”), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```
