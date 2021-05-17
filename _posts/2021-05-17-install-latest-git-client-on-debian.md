---
layout: post
title: "install latest git client on Debian"
tags: [dev, git]
---
# subject
install latest git client on Debian Linux OS

# purpose
install latest git client ( not 2.20.1 but 2.29.2+ ) 

# description
Debian not support default apt repository for latest git client.

```
$sudo apt install git -y
$git version
git version 2.20.1

$sudo apt -t buster-backports install git
$git version
git version 2.29.2
```

buster backport is here "deb http://ftp.debian.org/debian buster-backports main" on /ect/apt/sources.list
reference : https://unix.stackexchange.com/questions/559437/how-do-i-get-git-2-24-installed-on-debian-buster  
