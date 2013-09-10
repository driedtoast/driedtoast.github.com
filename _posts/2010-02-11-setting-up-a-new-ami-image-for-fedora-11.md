---
layout: post
title:  "Setting up a new AMI image for fedora 11"
date:   2010-02-11 08:23:00
categories:   aws,cloud,ecs,setup
---
Since its a bit of a pain to create the fedora 11 ami image for use in EC2, I thought I would share a script.

First part of the script sets up the variables used through script.
{% gist 360541 %}

In the above, you need to setup your keys and access keys for amazon. This is used later in the script to publish the image to the s3 bucket. It also assumes you have the ami tools downloaded and installed.  This also assumes you are using fedora 11 to build the image (I use parallels with fedora 11 on it).

Now we need to make an img and mount to it and push files to it.
{% gist 360542 %}

The above also sets up the fstab file and the directories we will use to add things to.

Next we setup the yum repo files and the start installing the fedora 11 package.
{% gist 360544 %}

The above also installs some base rpms. Now for the amazon parts such as the module and tools.
{% gist 360545 %}

Now we start modifying some of the base system files to work in EC2.
{% gist 360546 %}

Now for general customization and including of amazon scripts, which are described below.
{% gist 360547 %}

You can add your own little flare to the above section to talk to chef, puppet, or equivalent to install the rest of the server, its up to you.

Now ship it off to amazon, you'll have to register it once you are done.

{% gist 360548 %}

Below is the amazon setup script (awssetup) that is referenced above and will be executed on startup, taken from an amazon fedora 8 image, mostly verbatim.
{% gist 360550 %}

Here is the script for get-credentials.sh that is called in the above script, which is also found in a base amazon image.
{% gist 360553 %}

Works with the following:
* Kernel - aki-a71cf9ce
* Ramdisk - ari-a51cf9cc

