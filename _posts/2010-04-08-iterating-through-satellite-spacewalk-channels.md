---
layout: post
title:  "Iterating through Satellite/Spacewalk channels"
date:   2010-04-08 14:22:00
categories:   development,python,spacewalk,xmlrpc
---
Been having to work with spacewalk lately.

I wanted to sync the RPM packages up to an S3 bucket, so I wrote a script in python to iterate through the channels and push them.

This is just a snippet to get a list of channels and print out the rpm path.

{% gist 360560 %}

The RPC API is at [http://www.redhat.com/docs/en-US/Red_Hat_Network_Satellite/5.3/API_Overview/html/index.html](http://www.redhat.com/docs/en-US/Red_Hat_Network_Satellite/5.3/API_Overview/html/index.html).

Its fairly easy to use.
