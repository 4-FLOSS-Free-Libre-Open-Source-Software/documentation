---
title: "Userscripts"
description: "Invidious's Userscripts documentation."
lead: "Invidious's Userscripts documentation."
date:
lastmod:
draft: false
images: []
menu:
  docs:
    parent: "general"
weight: 100
toc: true
---

Download ViolentMonkey for your Browser:  
[Firefox](https://addons.mozilla.org/en-US/firefox/addon/violentmonkey/)  
[Chrome and Chromium](https://chrome.google.com/webstore/detail/violentmonkey/jinjaccalgkegednnccohejagnlnfdag)  
[Others](https://violentmonkey.github.io/get-it/)  

Than add the following script in ViolentMonkey. It will always add `&local=true` to the end of the video URL.

```
// ==UserScript==
// @name        Invidious Proxy automatically
// @match       *://*.invidio.us/watch?v=*
// @run-at      document-start
// @grant       none
// ==/UserScript==


if (!(/[?&]local=/).test(location.search) && !(/[?&]quality=dash/).test(location.search)) {
  location.search += (location.search ? "&" : "?") + "local=true";
}
```

You can also enable this by checking `Proxy videos?` in your preferences.
