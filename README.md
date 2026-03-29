<h1 align="center">chrlauncher</h1>

<p align="center">
	<a href="https://github.com/michatec/chrlauncher/releases"><img src="https://img.shields.io/github/v/release/michatec/chrlauncher?style=flat-square&include_prereleases&label=version" /></a>
	<a href="https://github.com/michatec/chrlauncher/releases"><img src="https://img.shields.io/github/downloads/michatec/chrlauncher/total.svg?style=flat-square" /></a>
	<a href="https://github.com/michatec/chrlauncher/issues"><img src="https://img.shields.io/github/issues-raw/michatec/chrlauncher.svg?style=flat-square&label=issues" /></a>
	<a href="https://github.com/michatec/chrlauncher/graphs/contributors"><img src="https://img.shields.io/github/contributors/michatec/chrlauncher?style=flat-square" /></a>
	<a href="https://github.com/michatec/chrlauncher/blob/master/LICENSE"><img src="https://img.shields.io/github/license/michatec/chrlauncher?style=flat-square" /></a>
</p>

-------

<p align="center">
	<img src="/images/chrlauncher.png?hgcv" />
</p>

### Description:
Small and very fast portable launcher and updater for Chromium.

### System requirements:
- Windows 7, 8, 8.1, 10, 11 32-bit/64-bit
- An SSE2-capable CPU
- KB3063858 update for Windows 7 was required [[x64](https://www.microsoft.com/en-us/download/details.aspx?id=47442) / [x32](https://www.microsoft.com/en-us/download/details.aspx?id=47409)]

### GPG Signature:
Binaries have GPG signature `chrlauncher.exe.sig` in application folder.

- Public key: [pubkey.asc](https://raw.githubusercontent.com/henrypp/builder/master/pubkey.asc) ([pgpkeys.eu](https://pgpkeys.eu/pks/lookup?op=index&fingerprint=on&search=0x5635B5FD))
- Key ID: 0x5635B5FD
- Fingerprint: D985 2361 1524 AB29 BE73 30AC 2881 20A7 5635 B5FD

### Default browser:
chrlauncher has feature to use portable Chromium as default browser and it will be open links from another programs through chrlauncher.
- start "SetDefaultBrowser.bat" (as admin).
- start "Control panel" -> "Default programs" -> "Set your default programs" -> "chrlauncher" and set all checkboxes on.

### Command line:
There is list of arguments overrides .ini options
~~~
-autodownload - auto download update and install it!
-bringtofront - bring chrlauncher window to front when download started
-forcecheck - force update checking
-wait - start browser only when check/download/install update complete
-update - use chrlauncher as updater, but does not start Chromium
~~~

### Supported browser:
- as launcher - Chromium based (like Google Chrome, Opera, Yandex Browser, Vivaldi, etc.) and Firefox based (Mozilla Firefox, Basilisk, Pale Moon, Waterfox, etc.)
- as updater - Chromium only

### Chrome++:
- By default Chromium encrypt profile with user SID, which is disabled by [Chrome++](https://github.com/Bush2021/chrome_plus), so it is recomended. Starting with version 2.7 of chrlauncher it added support of Chrome++.

### Settings:
~~~ini
[chrlauncher]

# Custom Chromium update URL (string):
#ChromiumUpdateUrl=https://chromium.woolyss.com/api/v3/?os=windows&bit=%d&type=%s&out=string

# Command line for Chromium (string):
# See here: https://peter.sh/experiments/chromium-command-line-switches/
ChromiumCommandLine=--flag-switches-begin --user-data-dir=..\profile --no-default-browser-check --disable-logging --no-report-upload --flag-switches-end

# Chromium executable file name (string):
ChromiumBinary=chrome.exe

# Chromium binaries directory (string):
# Relative (to chrlauncher directory) or full path (env. variables supported).
ChromiumDirectory=.\bin

# Set Chromium binaries architecture (integer):
#
# 0	-> autodetect (default)
# 64	-> 64-bit
# 32	-> 32-bit
ChromiumArchitecture=0

# Auto download updates if found (boolean)
#
# false	-> show tray tip if update found, downloading manually (default)
# true	-> auto download update and install it!
ChromiumAutoDownload=false

# Bring chrlauncher window when download started (boolean)
#
# false	-> don't bring main window to front automatically
# true	-> bring chrlauncher window to front when download started (default)
ChromiumBringToFront=true

# Set download in foreground mode (boolean):
#
# false	-> start browser and check/download/install update in background
# true	-> start browser only when check/download/install update complete (default)
ChromiumWaitForDownloadEnd=true

# Use chrlauncher as updater, but does not start Chromium (boolean):
#
# false	-> update & start Chromium (default)
# true	-> download & install Chromium update without start
ChromiumUpdateOnly=false

# Type of Chromium builds:
#
# dev-official
#	Official development builds from snapshots repository
#	"storage.googleapis.com/chromium-browser-snapshots/index.html" (32/64 bit)
#
# stable-codecs-sync
#	Unofficial stable builds with codecs
#	"github.com/Hibbiki/chromium-win64/releases" (64 bit)
#	"github.com/Hibbiki/chromium-win32/releases" (32 bit)
#
# dev-nosync
#	Unofficial development builds without Google services
#	"github.com/RobRich999/Chromium_Clang/releases" (32/64 bit)
#
# dev-codecs-sync
#	Unofficial development builds with codecs and without Google services
#	"github.com/macchrome/winchrome/releases" (64 bit)
#
# dev-codecs-nosync
#	Unofficial development builds with codecs and without Google services
#	"github.com/macchrome/winchrome/releases" (64 bit)
#
# ungoogled-chromium
#	Unofficial builds without Google integration and enhanced privacy (based on Eloston project)
#	"github.com/macchrome/winchrome/releases/" (32/64 bit)
#	"github.com/Eloston/ungoogled-chromium"
ChromiumType=dev-official

# Check for new Chromium version once in X days (integer):
#
# 2	-> check updates once in a X days (default)
# 0	-> disable update checking
# -1	-> force update checking
ChromiumCheckPeriod=2

# Last cached update checking timestamp (integer):
ChromiumLastCheck=0

# Start browser when downloading and installing is over (boolean)
#
ChromiumRunAtEnd=true

# A DLL hijack implements Chrome full portability as well as tab enhancements.
# https://github.com/Bush2021/chrome_plus
#ChromePlusDirectory=.\chrome_plus

#
# Internal settings (SDK)
#

# Set custom useragent (string):
#UserAgent=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.0.0 Safari/537.36

# Set proxy configuration (string):
#Proxy=127.0.0.1:80
~~~
(c) 2015-2026 Michatec
This is a fork of the original [Repo](https://github.com/henrypp/chrlauncher).
