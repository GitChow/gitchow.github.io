---
layout: post
title:  "Chrome Extension to export Perfect Resume Export From LinkedIn"
date:   2016-08-15 21:18:15 +0800
categories: jekyll update
tags: [Chrome,LinkedIn]

---

I don't know since when I started to use LinkedIn, but I just remember the first time I saw it, I liked it a lot.
WHY? because the CV structure is made so clear and so comprehensive, so you won't miss or mess anything. Neat!

everything goes well until one day I find I want to get a new job: there should be an export function existing?
Yes, right, there is. BUT... the layout really sucks: WHY? 
my exported one is **6 pages** and it's hardly readable due to the bad structure.(maybe the paied subscription is much better...?)

After trying out existing one in Chrome extension store, I decided to reinvent the wheel.

Here comes my version of chrome extension to have perfect CV export from LinkedIn:

check out https://github.com/GitChow/PrintNicely

so, a quick figure, after using this, my CV comes to **2** pages.here is how it looks like:
![optimized CV part 1](https://gitchow.github.io/images/linkedin_cv_chrome/optimizedResume_part1.png)
![optimized CV part 2](https://gitchow.github.io/images/linkedin_cv_chrome/optimizedResume_part2.png)

techical part, basically both new css and javascript are injected into the web page to re-layout and also mapulate some data(contact section)

to build the chrome extension, the first important file is "manifest.json", where you define
- your extension name/description/version
- permission
- background script (most important for this case, to call script)

and in background script, the inject js and css file is defined

```javascript
chrome.browserAction.onClicked.addListener(function(tab) {
  chrome.tabs.executeScript(null, {file: "inject.js"});
  chrome.tabs.insertCSS(null, {file: "inject.css"});
});
```

so, we can do a lot via js and css injection, maybe even design some CV template to sell?! :smile::smile: