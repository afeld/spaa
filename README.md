!SLIDE

# Single-Page App Architecture

## Aidan Feldman
Senõr Web Developer, [Jux](https://jux.com)

View at [github.com/afeld/spaa](https://github.com/afeld/spaa)

!SLIDE

Going to attempt to hit *every JS-related buzzword* in 30 mins

!SLIDE

# The bliss of traditional sites

* Frequent page loads
    - Get new code quickly
    - Garbage collection not necessary
* Only load relevant markup/files

!SLIDE

# Client⟺Server Data Passing

* Script tags
    - no page caching
* AJAX
* Web Sockets

!SLIDE

# Templates

* Compiled templates
* Logic-less template
    * [Mustache](http://mustache.github.com/)
* Language-agnostic templates
    * a.k.a. their own language
* Shared templates
    - e.g. Jux's gallery CSS
* [HTML5 `<template>`](http://www.html5rocks.com/en/tutorials/webcomponents/template/)
    - super-new (Chrome only)

!SLIDE

# Why server-side rendering?

* Crawlers
    - Google's "AJAX crawling"
* Supa-fast rendering time
    - Twitter's "Time to First Tweet"
* Any language!
* Take rendering load off server

!SLIDE

# Why client-side rendering?

* Replacing values w/ jQuery doesn't get very far
* Need immediate feedback to interaction
* Frequently updating display of data
* Transitions between "pages"

!SLIDE

# Hybrid rendering

* [PJAX](http://pjax.heroku.com/)
* Caching

!SLIDE

* MVC vs MV*
* Routers
* Widgets
    - Dojo
    - jQuery UI

!SLIDE

# View updating

* Evented
    - Backbone
* Client-side data binding
    - Angular & Ember
* Full-stack data binding
    - [Derby](http://derbyjs.com/) and [Meteor](http://meteor.com/)

!SLIDE

# Loading

Concatenation + minification.  Duh.

!SLIDE

# Dependency management

* Module loaders
    - CommonJS
    - AMD
* Whole slew of package managers
    - Bower, Jam, Volo, Ender, ComponentJS
    - Good comparison in [Yeoman docs](http://yeoman.io/packagemanager.html)

!SLIDE

# Additional resources

* [Single page apps in depth](http://singlepageappbook.com/)

!SLIDE

# Fin.

Aidan Feldman

[@aidanfeldman](https://twitter.com/aidanfeldman)

[afeld.me](http://afeld.me)
