---
layout: post
title: Visual Code Studio
date:   2016-05-15 18:07:08 +0100
categories: visual code studio
location: On a train from London to Bath
---

I'm a convert! Visual Code Studio rocks. My colleague
[Maciej](https://github.com/graforlock) mentioned to me
that he was using Visual Code studio instead of Atom. I can see why. It's fast.
None of this faffing, waiting for Atom to decide what to do, just pure and
simple editing delight.

I've customised a few key bindings to make my life a little Emacs more
friendly:

{% highlight json %}
[
   { "key": "ctrl+i", "command": "actions.find"},
   { "key": "ctrl+a", "command": "cursorHome"},
   { "key": "ctrl+e", "command": "cursorEnd"},
   { "key": "ctrl+n", "command": "scrollLineDown"},
   { "key": "ctrl+p", "command": "scrollLineUp"},
    {
        "key": "ctrl+n",
        "command": "cursorDown",
        "when": "editorTextFocus"
    },
    {
        "key": "ctrl+p",
        "command": "cursorUp",
        "when": "editorTextFocus"
    }
]
{% endhighlight %}

I'll be honest. It's a little odd that your tabs are under the "Working Files"
section on the left, it's odd that `Ctrl+Tab` will open a blank file. But
these are definitely things I can work around.

Also... Intellisense is great. The autocomplete is great... at least for
JS/HTML. Python and Golang are really important languages for me and they have
good extensions which provide everything I need.

### Did you say it has an inbuilt `diff` editor?

That's build in. I'm pretty stoked about that!

### Did you say it's fast?

Yep, it really is.

### Did you say fewer plugins with a performance boost?

You're correct. Thanks Microsoft (wow that's werid to write).

### Conclusion

Coming from an IT support role, to running a Microsoft/Linux infrastructure,
to using solely open source software I cannot commend Microsoft highly enough
for this piece of software. It blows Atom and Sublime Text out of the way...
Allbeit Sublime Text led the way (I even bought a license it was that great).

You should definitely give it a go.