---
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: id_What_is_this
title: "downgrade ubuntu!"

# post specific
# if not specified, .name will be used from _data/owner/[language].yml
author: lisir
# multiple category is not supported
category: lisir
# multiple tag entries are possible
tags: [heng, example post, sample, test]
# thumbnail image for post
img: ":post_pic3.jpg"
# disable comments on this page
#comments_disable: true

# publish date
date: 2022-09-16 22:04:30 +0900

# seo
# if not specified, date will be used.
#meta_modify_date: 2022-01-01 10:04:30 +0900
# check the meta_common_description in _data/owner/[language].yml
#meta_description: ""

# optional
# if you enabled image_viewer_posts you don't need to enable this. This is only if image_viewer_posts = false
#image_viewer_on: true
# if you enabled image_lazy_loader_posts you don't need to enable this. This is only if image_lazy_loader_posts = false
#image_lazy_loader_on: true
# exclude from on site search
#on_site_search_exclude: true
# exclude from search engines
#search_engine_exclude: true
# to disable this page, simply set published: false or delete this file
# published: false
---
<!-- outline-start -->

This is a guide to downgrade Ubuntu system version. I downgrade it from 22.04.5 to 22.04.1. 

First step is to downgrade sources list file to the previous version. You can find the code for each version on ubuntu website(https://releases.ubuntu.com/). The 22.04.5 is focal and the 22.04.1 is jammy. Using the following command to see your version code:   
```cat /etc/os-release | grep -i version ```   
It will print the version in you console:   
```
VERSION_ID="22.04"
VERSION="22.04.1 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
```

Then, use following command to change the source list:   
```$ sudo sed -i 's/cosmic/bionic/g' /etc/apt/sources.list ```      

You can check the result by using following commnad after change:   
```cat /etc/apt/sources.list | grep -v ^# | grep . ```      

It will print like this:   
``` 
deb http://cn.archive.ubuntu.com/ubuntu/ jammy main restricted
deb http://cn.archive.ubuntu.com/ubuntu/ jammy-updates main restricted
deb http://cn.archive.ubuntu.com/ubuntu/ jammy universe
deb http://cn.archive.ubuntu.com/ubuntu/ jammy-updates universe
deb http://cn.archive.ubuntu.com/ubuntu/ jammy multiverse
deb http://cn.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
deb http://cn.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu jammy-security main restricted
deb http://security.ubuntu.com/ubuntu jammy-security universe
deb http://security.ubuntu.com/ubuntu jammy-security multiverse
```
The jammy code is already in the source list.


Then use the following 3 command to downgrade your system:   
```
sudo apt update
sudo apt upgrade
sudo apt dist-upgrade
```   

Reboot your system.
