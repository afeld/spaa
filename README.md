!SLIDE

# Single-Page App Architecture

## Aidan Feldman

View at [github.com/afeld/spaa](https://github.com/afeld/spaa)

!SLIDE

# moi

* Senõr Web Developer, [Jux](https://jux.com)
* Instructor, [General Assembly](https://generalassemb.ly/) and [NYU](http://scps.nyu.edu/)
* Author, *[Developing a Backbone.js Edge](http://bleedingedgepress.com/our-books/)* (coming soon!)

!SLIDE

Going to attempt to hit *every JS-related buzzword* in 30 mins

!SLIDE

How many consider themselves "advanced" in JS?

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
    - Garbage collection not necessary
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

!SLIDE

# Client⟺Server Data Passing (cont.)

* Script tags

------------

    @@@html
    <script>
      myInitFunction({
        data1: <%= data1_obj %>,
        data2: <%= data2_obj %>,
        ...
      });

      // or

      myGlobal = {
        data1: <%= data1_obj %>,
        data2: <%= data2_obj %>,
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
* Logic-less template
    * [Mustache](http://mustache.github.com/), [Handlebars](http://handlebarsjs.com/)
* Language-agnostic templates
    * a.k.a. their own language
* Shared templates
    - e.g. Jux's gallery CSS

!SLIDE

# Template Passing

* Pre-compiled as JS functions
* [HTML5 `<template>`](http://www.html5rocks.com/en/tutorials/webcomponents/template/)
    - super-new (Chrome only)

!SLIDE

# Why server-side rendering?

* Crawlers
    - [Google's "AJAX crawling"](https://developers.google.com/webmasters/ajax-crawling/)
* Supa-fast rendering time
    - [Twitter's "Time to First Tweet"](http://engineering.twitter.com/2012/05/improving-performance-on-twittercom.html)
* Any language!

!SLIDE

# Why client-side rendering?

* `jQuery.html()` doesn't get very far
* Need immediate feedback to interaction
* Frequently updating display of data
* Transitions between "pages"
* Take rendering load off server\*

!SLIDE

# Hybrid rendering

* Still get page caching
* Options:
    - Server rendering, client updating
    - [PJAX](http://pjax.heroku.com/)

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
    - Angular & Ember
* Full-stack data binding
    - [Derby](http://derbyjs.com/) and [Meteor](http://meteor.com/)

!SLIDE

# Evented

## Backbone

    @@@javascript
    var $name = this.$('.name');
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

## RequireJS

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

* Think Pip, Maven, Rubygems, NPM, etc.
* Whole slew of them: Bower, Jam, Volo, Ender, ComponentJS
* Good comparison in [Yeoman docs](http://yeoman.io/packagemanager.html)

!SLIDE

# Add'l resources

* [Single page apps in depth](http://singlepageappbook.com/)

!SLIDE

# Fin.

Aidan Feldman

[@aidanfeldman](https://twitter.com/aidanfeldman)

[api.afeld.me](http://api.afeld.me)

[github.com/afeld/spaa](https://github.com/afeld/spaa)
