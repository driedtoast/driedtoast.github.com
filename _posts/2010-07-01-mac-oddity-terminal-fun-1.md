---
layout: post
title:  "Mac oddity - Terminal Fun 1"
date:   2010-07-01 06:51:00
categories: mac, shell
---

So I was looking at my files today via the terminal and noticed an @ sign next to one of the files. This is sort of odd since the file was just a text file and I downloaded it as part of an open source project.

Check it:

{% gist 459988 %}

Notice the special apple command `ls -@` to show the details of what that @ means. It indicated extra metadata on the file. Thanks to <a href="http://www.flester.com/blog/2008/01/03/mac-os-x-leopard-ls1-output">Flester's blog</a> on the post.

Some other details of the @ sign is over on <a href="http://www.macosxhints.com/article.php?story=20071029151619619">mac hints</a>.

I fixed it just by `cat changes.txt &gt; newfile.txt; rm changes.txt; mv newfile.txt changes.txt`.

Also for the finderinfo 32 

{% highlight sh %} 
mkdir temp
cp file temp/
cp -XR temp newtemp

cd newtemp
ls -@l
{% endhighlight %}

Sourced from: <a href="http://forums.macrumors.com/showthread.php?t=841825" rel="nofollow">http://forums.macrumors.com/showthread.php?t=841825</a>