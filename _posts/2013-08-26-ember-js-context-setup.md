---
layout: post
title:  "Setting up a context object in emberjs"
date:   2013-08-26 18:04:33
categories: emberjs, javascript
---

So, I started messing with [emberjs](http://emberjs.com) recently to prototype some UI functionality that relies on a REST backend. The backends server's session id for the browser is established through a rails app that is at a different subdomain. Essentially the setup would be login.prototype.dev and then redirect to a node js app presenting an emberjs app (app.prototype.dev). The reason for the different domains is to allow an existing app to go along as normal while experimenting with different display options via the nodejs / emberjs app.

Here are a couple things I needed to do with my prototype:

* Establish a user object I could use to know what context calls will be made from
* Point the rest calls to a different REST domain server (using pow.cx for different domains locally)
* Display data from the existing REST service

**First off,** [emberjs](http://emberjs.com) makes much of the data and element binding pretty easy to do. So easy that it makes you second guess what is actually working. That easy of use drops flat though when you do something a bit outside the norm. If you aren't drinking the complete coolaid of ember's conventions, you are stuck hunting around for customization options.

**Initializing** the application was the first issue to solve. I wanted to load the user data after ember has setup the framework. In order to do that ember has the concept of an [application initializer](http://emberjs.com/api/classes/Ember.Application.html), which helps to accomplish the goal of loading the data when everything is ready. 

Example: 

{% highlight coffeescript %} 
window.App = Ember.Application.create
  rootElement: '#ember-app'

window.Context = {}

App.User = DS.Model.extend

App.initializer 
  name: "context:setup",
  initialize: (container, application) ->
  	users = App.User.find({}) 
	users.on 'didLoad', () -> 
      Context.user = users.get("firstObject")
{% endhighlight %}

_[NerdyWorm](http://nerdyworm.com/blog/2013/04/03/ember-initializers/) has a decent writeup on the initializer and ordering of the initialization steps as well._

**Ember Data** is a little buggy, hence in the above example there is a `{}` passed to the find to trigger the event callbacks. It ends up doing an empty query, whereas the normal `.find()` will always result in a live array. Convention is very important with ember data as it requires the responses to have a format designed based on the naming of the model.

Example for a query / list find (`find({})` or `find()`):

{% highlight json %} 
{
   "users": [  { "id": 1, "name": "John Doe"} ]	
}
{% endhighlight %}

Example for a single find query (`find(1)`):

{% highlight json %} 
{
   "user": { "id": 1,  "name": "John Doe" }
}
{% endhighlight %}

I'll write about the data customization for the `RESTAdapter` a little later. Hope this helps others with getting going on emberjs.
