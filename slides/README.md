!SLIDE

# Single-Page App Architecture

## Aidan Feldman

[github.com/afeld/spaa](https://github.com/afeld/spaa)

!SLIDE

# moi

* Education Hacker, [GitHub](https://github.com)
* Instructor, [NYU](http://scps.nyu.edu/)
* Author, *[Developing a Backbone.js Edge](http://bleedingedgepress.com/our-books/)*

!SLIDE

Going to attempt to hit *every JS-related buzzword* in 30 mins

~~~SECTION:notes~~~

TODO change to a clock icon

~~~ENDSECTION~~~

!SLIDE

How many consider themselves "advanced" in JS?

~~~SECTION:notes~~~

I use airquotes because there's no good way to measure level.

~~~ENDSECTION~~~

!SLIDE

Clarifying questions OK, but save bigger stuff for the end

!SLIDE

[But first...](https://sphotos-b.xx.fbcdn.net/hphotos-ash3/575026_10200709299914001_991887145_n.jpg)

!SLIDE

# Why!?

!SLIDE

# The bliss of traditional sites

* Frequent page loads
    - Get new code quickly
    - Stateless
* Only load relevant markup/files

!SLIDE

# Client⟺Server Data Passing

* Extract from server-rendered DOM

------------

    @@@html
    <h1>Welcome, <span class="name">Aidan</span>!</h1>
    ...
    <label for="name">Name</label>
    <input type="text" name="name" value="Aidan Feldman" />

!SLIDE

# Client⟺Server Data Passing

* Extract from server-rendered DOM
    - Which is canonical?

~~~SECTION:notes~~~

TODO show w/ arrow in previous slide

~~~ENDSECTION~~~

!SLIDE

# Client⟺Server Data Passing (cont.)

* Script tags

------------

    @@@html
    <script>
      myInitFunction({
        data1: <%= data1_obj %>,
        ...
      });

      // or

      myGlobal = {
        data1: <%= data1_obj %>,
        ...
      };
    </script>

!SLIDE

# Client⟺Server Data Passing (cont.)

* Script tags
    - data available immediately
    - tough to do page caching

!SLIDE

# Client⟺Server Data Passing (cont.)

## Async

* AJAX
* Web Sockets
    - push support
    - arguably better for notifications than CRUD

!SLIDE

# Templates

* JS-only (browser or NodeJS)
    * [Jade](http://jade-lang.com/), [EmbeddedJS (EJS)](http://embeddedjs.com/), [Underscore](http://documentcloud.github.com/underscore/#template), ...
* Logic-less/language-agnostic template
    * [Mustache](http://mustache.github.com/), [Handlebars](http://handlebarsjs.com/), Liquid
* Shared templates
    * e.g. Jux's gallery CSS

~~~SECTION:notes~~~

TODO add link for Liquid

~~~ENDSECTION~~~

!SLIDE

# Template Passing

* Script tags

---

    @@@html
    <script type="text/template" id="my-template">
      <div>{{ replace_me }}</div>
    </script>

!SLIDE

# Template Passing (cont.)

* Pre-compiled

---

    @@@javascript
    JST = {};
    JST['myTemplate'] = function(context){
      return '<div>concat' + context.val + 'strings</div>';
    };

    var markup = JST['myTemplate']({ val: 'some' });

!SLIDE

# Template Passing (cont.)

* Script tags
* Pre-compiled
* [HTML5 `<template>`](http://www.html5rocks.com/en/tutorials/webcomponents/template/)
    - Chrome only

~~~SECTION:notes~~~

TODO verify still Chrome only, and be clear on difference from `<script>`

~~~ENDSECTION~~~

!SLIDE

# Page Load Times

!SLIDE

## [motherf\*ckingwebsite.com](http://motherfuckingwebsite.com)

![motherfuckingwebsite.com](images/mfw_network.png)

~~~SECTION:notes~~~

Network tab in Chrome Dev Tools

~~~ENDSECTION~~~

!SLIDE

## GMail

![gmail](images/gmail_network.png)

~~~SECTION:notes~~~

DOMContentReady is almost 2s in

~~~ENDSECTION~~~

!SLIDE

## [motherf\*ckingwebsite.com](http://motherfuckingwebsite.com)

![motherfuckingwebsite.com](images/mfw_paint.png)

~~~SECTION:notes~~~

Timeline tab in Chrome Dev Tools

~~~ENDSECTION~~~

!SLIDE

## GMail

![gmail](images/gmail_paint1.png)

~~~SECTION:notes~~~

can't start painting until almost 1.5s in

~~~ENDSECTION~~~

!SLIDE

## ...

![gmail](images/gmail_paint2.png)

~~~SECTION:notes~~~

continues painting up past 6s

~~~ENDSECTION~~~

!SLIDE

# Why server-side rendering?

* Crawlers
    - [Google's "AJAX crawling"](https://developers.google.com/webmasters/ajax-crawling/)
* Cleanup is free (stateless)
* Supa-fast rendering time
    - [Twitter's "Time to First Tweet"](http://engineering.twitter.com/2012/05/improving-performance-on-twittercom.html)
* Any language!

!SLIDE

# Why client-side rendering?

* `jQuery.html()` doesn't get very far
* Immediate feedback
* Live-updating
* Transitions
* Take rendering load off server\*

~~~SECTION:notes~~~

still need an API

~~~ENDSECTION~~~

!SLIDE

# Hybrid rendering

* Server rendering, client updating
* Can still cache pages
* Options:
    - Shared code on client + server
    - [PJAX](http://pjax.heroku.com/)

~~~SECTION:notes~~~

server renders intial pageload, client handles navigation

~~~ENDSECTION~~~

!SLIDE

# JS Structure

* MVC, MV*
* Routers
    - URL serialization
* Widgets
    - Dojo, jQuery UI

!SLIDE

# View updating

* Evented
    - Backbone
* Client-side data binding
    - Angular, Ember
* Full-stack data binding
    - [Derby](http://derbyjs.com/), [Meteor](http://meteor.com/)

!SLIDE

# Evented

## Backbone

    @@@javascript
    var $name = $('.name');
    user.on('change:name', function(user, newName){
      $name.text(newName);
    });

!SLIDE

# Data binding

## Angular

    @@@html
    <input type="text" ng-model="yourName" placeholder="Enter name">
    <h1>Hello {{yourName}}!</h1>

Look ma, no glue code!

!SLIDE

# Loading

Concatenation + minification.  Duh.

!SLIDE

# Dependency management

* Module loaders
  - CommonJS
  - Asynchronous Module Definition (AMD)

!SLIDE

# Dependency management (cont.)

## RequireJS (AMD)

    @@@javascript
    require(['dependency.js'], function(dependency){

      // do stuff

      dependency.on('someEvent', function(){
        require(['another.js'], function(another){
          another.doStuff();
        });
      });

    });

!SLIDE

# Package managers

* Think Pip, Maven, Rubygems, etc.
* Jury is out
    * Bower, Jam, Volo, Ender, ComponentJS, NPM
* Good comparison in [Yeoman docs](http://yeoman.io/packagemanager.html)

!SLIDE

# Add'l resources

* [Single page apps in depth](http://singlepageappbook.com/)
* [Deploying JavaScript Applications](http://alexsexton.com/blog/2013/03/deploying-javascript-applications/)

!SLIDE

# Fin.

Aidan Feldman

[@aidanfeldman](https://twitter.com/aidanfeldman)

[api.afeld.me](http://api.afeld.me)

[github.com/afeld/spaa](https://github.com/afeld/spaa)
