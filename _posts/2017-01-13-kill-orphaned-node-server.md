---
layout: post
title: "Find and kill an orphaned node server"
description: "Hunt down and kill an orphaned node server. Kill it with fire."
tags: [node, npm, reminder]
---

I recently ran into an issue where I was using an `npm` script to start an instance of a node [http-server](https://github.com/indexzero/http-server). Unfortunately the script was erroring out without killing the server. After running the script several times I had a number of servers running on various ports that were just running in the background. If you run into a simple scenario, you can find them and kill them like this:

I knew I had an instance running on port `8082`

```
$ lsof -i tcp:8082

COMMAND   PID     USER   FD   TYPE             DEVICE SIZE/OFF NODE NAME
node    50568 sanbornh   13u  IPv4 0x7adae33acae706b1      0t0  TCP *:sunproxyadmin (LISTEN)
```

Now you can simply kill the server based on its `PID`


```
$ kill 50568

http-server stopped.
```