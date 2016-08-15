---
layout: post
title:  "Chrome extension to export perfect resume from LinkedIn"
date:   2016-08-15 21:18:15 +0800
categories: jekyll update
tags: [Chrome,LinkedIn]

---
![this is a such cover image, just play around](https://gitchow.github.io/images/linkedin_cv_chrome/perfect-resume.png)


I don't know since when I started to use LinkedIn, but I just remember the first time I saw it, I liked it a lot.
WHY? because the profile structure is made so clear and information fields are comprehensive, that you won't miss or mess anything. Neat!

Everything went well until one day I wanted to get a new job: there should be an export function provided?
Yes, there is. BUT... the layout really sucks: 
My exported one is **6 pages** and it's hardly readable due to the bad structure.(maybe the paied subscription is much better...?:sweat_smile:)

After trying out some options in Chrome extension store, I decide to reinvent the wheel.

Here comes my version of chrome extension to make perfect resume export from LinkedIn:

check out [https://github.com/GitChow/PrintNicely](https://github.com/GitChow/PrintNicely)

so, a quick figure, after using this, my resume comes to **2 pages**. here is how it looks like:

![optimized CV part 1](https://gitchow.github.io/images/linkedin_cv_chrome/optimizedResume_part1.png)
![optimized CV part 2](https://gitchow.github.io/images/linkedin_cv_chrome/optimizedResume_part2.png)

techical part: both new css and javascript are injected into the web page to re-layout and also mapulate some data(contact section)

to build the chrome extension, the first important file is "manifest.json", where you define

- your extension name/description/version
- permission
- background script (most important for this case, to call script)

and in background script, the injected js and css file are defined

```javascript
chrome.browserAction.onClicked.addListener(function(tab) {
  chrome.tabs.executeScript(null, {file: "inject.js"});
  chrome.tabs.insertCSS(null, {file: "inject.css"});
});
```

hmmm, maybe I need to design and implement some more sexy resume template to sell?! :scream::scream: