---
layout: post
title:  "Workaround for NX Capslock problem"
date:   2011-02-15 06:21:00
categories: remote desktop, development
---
Create a script for your path, like so:

{% highlight sh %} 
#!/bin/sh
xsendkeycode 66 1
xsendkeycode 66 0
{% endhighlight %}

and install `lineakd` (which contains the xsendkeycode).