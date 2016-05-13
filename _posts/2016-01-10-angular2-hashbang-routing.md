---
author: ""
date: "2016-01-10T16:13:51Z"
description: ""
tags: angular2
title: "angular2 hashbang routing"
type:  "post"
location: On a train to Wigan
---

Angular2 defaults standard URL routing, but with my projects I don't want to have to set anything up in order to
get going.

I've been doing this for my projects as it allows me to swap the `LocationStrategy` on an off as I need it.

{% highlight typescript %}
import {bootstrap} from 'angular2/platform/browser'
import {provide} from 'angular2/core';
import {ROUTER_PROVIDERS, LocationStrategy, HashLocationStrategy} from 'angular2/router';
import {HTTP_PROVIDERS} from 'angular2/http';

bootstrap(AppComponent, [
    ROUTER_PROVIDERS,
    HTTP_PROVIDERS,
    provide(LocationStrategy, {useClass: HashLocationStrategy})
]);
{% endhighlight %}

URL Rewriting is a powerful concept, but I reckon that you only really need it for Apps. Not my
little side projects.
