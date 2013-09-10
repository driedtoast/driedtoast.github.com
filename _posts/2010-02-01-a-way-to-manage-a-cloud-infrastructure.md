---
layout: post
title:  "A way to manage a cloud infrastructure"
date:   2010-02-01 13:47:14
categories:   
---
<p>As I was looking for other projects out there to see if I was being redundant with the teaparty project on github, I found [scalr](https://scalr.net/). Its a commercial product and has some similar concepts that I was thinking of adding to my own project, but some of the concepts are not really done.</p>
<p>The application management and role management is a bit weak and the infrastructure is based on crontabs with curl calls to a php app for config registration and such. They could of done a lot better relying on a 3rd party configuration management tool such as cobbler, puppet or chef.</p>
