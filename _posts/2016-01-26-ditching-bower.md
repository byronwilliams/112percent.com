---
author: ""
date: "2016-01-26T08:31:24Z"
description: ""
tags: ["bower", "npm", "JavaScript"]
title: "ditching bower"
type: "post"
---

`bower` used to be my best friend. I'd use it for all of the frontend modules
I needed and I'd use `npm` to for all of my build packages.

I liked using `bower` as it provided a clear separation of concerns of packages.
But now it's another dependency what I don't really need in my life. `npm`
is pretty good at installing packages you need, it makes sense to keep all of the
front end packages in the same place as the back end one. At the end of the day
they're just JavaScript files. Having them kept all in one place makes everybodies
lives easier.

Maybe it's looking into things too much, but using separate tools separates us as
developers. Node devs write JavaScript, front end devs write JavaScript. I think
it's best that they stick to similar workflows.

I'm **removing** `bower` from all of my projects and **only** using
`npm` from now on.
