---
layout: post
title: "use winget for windows package manager"
tags: [dev, windows]
---
# subject
use winget for windows package manager

# purpose
use winget for windows package manager

# description
'winget' is new package manager for MS Windows
available for Windows 10 1709(10.0.16299) or over version

install from github release page
https://github.com/microsoft/winget-cli/releases/ 
or direct ms-appinstaller:?source=https://aka.ms/getwinget

usage
```
# search
$winget search vscode 
or
$winget search "Visual Studio Code" 

# install
$ winget install --moniker vscode-insiders --scope machine -i # scope: user/machine : interactive 

# upgrade
$ winget upgrade --all 

# uninstall
$ winget uninstall "Visual Studio Code"
```
#reference
https://devblogs.microsoft.com/commandline/windows-package-manager-1-0/ 
https://docs.microsoft.com/ko-kr/windows/package-manager/winget/
