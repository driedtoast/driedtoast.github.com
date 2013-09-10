---
layout: post
title:  "Open Shift Express with Identity Cert project"
date:   2011-05-11 09:42:00
categories: identity, development, openshift
---

<p>I decided to test out openshift offering by redhat. It runs python via the wsgi framework approach. So I decided to try and deploy the <a href="//github.com/driedtoast/identitycert">Identity Cert</a> project I'm working on.</p>
<p>After a couple changes in the application startup / library configuration based on <a href="//github.com/driedtoast/pytoaster">PyToaster</a>. I was ready to deploy. (Still need to incorporate the changes back into pytoaster project from identity cert for next projects I do, also some duplicate code cleanup)</p>
<p>Here is some of the steps I ended up having to do:</p>
<ul>
<li>In identity cert project, grab a copy: `git archive --format zip --output ~/temp/identitycert.zip master`</li>
<li>Create project for open shift:  `rhc-create-app -a osidentitycert -t wsgi-3.2.1`</li>
<li>`cd osidentitycert`</li>
<li>Add files from identity cert repo: `unzip ~/temp/identitycert.zip`</li>
<li>Resolve depends: `./bin/resolvedepends`</li>
<li>Add everything: `git add .` </li>
<li>Commit all: `git commit -m"initial commit"` </li>
<li>Add to open shift: git push</li>
</ul>
<p>So now its up at: <a href="http://osidentitycert-driedtoast.rhcloud.com/">http://osidentitycert-driedtoast.rhcloud.com/</a>. App still needs a bit of work though. Now I have some motivation to complete it.  Some gotchas I had to deal with:</p>
<ul>
<li> Pathing of files, used `os.path.dirname(__file__)` to get abs paths</li>
<li> Debugging of app, have to download app via `rhc-snapshot -a osidentitycert` (which downloads a tar you look into appname/logs) </li>
<li> Forgot my url for testing it, used `rhc-user-info` to find it</li>
</ul>
<p>Overall its still a bit clunky of a service, all command line (would be nice to have a little dashboard for quick url viewing) and debugging is a bit annoying.</p>