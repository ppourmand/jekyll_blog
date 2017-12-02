---
layout: post
title: Code Signing
permalink: /blog/2
---

Recently I've been making a tool that helps check to see if certain files are code signed properly. On MacOS, you use `codesign` on the command line, and on Windows you use their own `signtool.exe`. I wrapped both functionalities in an app built with the Electron framework so I can create a platform-agnostic codebase. The GUI component is built using bootstrap since I didn't really want to spend a ton of time on it. 

After I had built a usable 1.0 version of the application, I started running it on random `.app` files on my computer. Lots of apps seemed to be signed properly, but one thing did catch my eye. When running `Google Chrome.app` through my tool, I received the following result:

```
Google Chrome.app/: resource envelope is obsolete (custom omit rules)
```

That's.. weird. I've never seen that output before, usually when something is unsigned, a different error will be outputted.

Maybe I messed something up? So I re-downloaded chrome. I ran the tool on the `.dmg` file and it looked good but once again on the `.app`, it gave me the same error. Alright, time to go google (ha!) this to find out what it is I'm seeing. What I found is this [post](https://stackoverflow.com/questions/27946262/check-signature-tool-fails-with-message-resource-envelope-is-obsolete-custom-o). Interesting, so google is using a "version 1" signature? I don't know enough about this topic to say that this is a huge issue but it is a little concerning.

Just some food for thought.

Peace.

-P
