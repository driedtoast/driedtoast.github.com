---
layout: post
title:  "Quick Pinterest based column in css"
date:   2013-10-05 18:04:33
categories: css, sass
---

Let's first start off with saying this approach isn't for everyone. There are some compatibility issues for IE browsers, but in general it will work for anything that is within the technology of this century. The approach is to create all items in the columns as a list structure and to make that structure to appear like the pinterest column design.

First off is setting up the markup. We will just setup a simple `ul`, see below.

{% highlight html %} 
<ul class="make-me-pretty">
	<li><span class="title">Title A</span> Description of A </li>
	<li><span class="title">Title B</span> Description of B </li>
	<li><span class="title">Title C</span> Description of C </li>
	<li><span class="title">Title D</span> Description of D </li>
</ul>
{% endhighlight %}

Let's dive into how we will style it. We want to set the list to say its column based so it wraps like a newspaper. For all the items in the list it will wrap around a column structure.

{% highlight sass %} 
.make-me-pretty
  column-count: $column-count
  column-gap: $column-gap
  -moz-column-count: $column-count
  -moz-column-gap: $column-gap
{% endhighlight %}

What you will notice is that the wrap cuts off some of the elements on to different columns. In order to prevent that individual item from wrapping into 2 parts we set the style of the `li`.

{% highlight sass %} 
.make-me-pretty li
  display: block
{% endhighlight %}


There you have it, column based design without a lot of effort. You can style the `li` pretty much how you want.