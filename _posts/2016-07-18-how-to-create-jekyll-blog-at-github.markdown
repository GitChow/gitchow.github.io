---
layout: post
title:  "How to create Jekyll blog and host at Github"
date:   2016-07-18 21:49:15 +0800
categories: jekyll blog github
---


- create a repo at github, with name $username.github.io `$username` is your github account name
- clone this repo to your local drive, here let's say `D:/$username.github.io`
  - `git clone https://github.com/$username/$username.github.io.git`
- at your local laptop, install Jekyll, `gem install jekyll`
- change directory to `D:`, create jekyll site here: `jekyll new $username.github.io`
- commit, push all the files to remote `https://github.com/$username/$username.github.io.git`
- now you can access https://$username.github.io (in my case: https://gitchow.github.io)



[Jekyll website](https://jekyllrb.com/)