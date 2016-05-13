---
layout: post
title:  "Ionic + DefaultValueAccessor"
date:   2016-05-12 18:07:08 +0100
categories: ionic, angular2
location: Bath, England
---

When nesting Ionic `ion-` components within other Angular2 components you can run into a few issues such as `No value accessor for '' in [searchQuery in SearchbarComponent@0:15]`

Take this example:

searchbar.html

{% highlight html %}
<ion-searchbar [(ngModel)]="searchQuery"
               (input)="filterItems($event)">
</ion-searchbar>
{% endhighlight %}
SearchbarComponent.js

{% highlight javascript %}
import {EventEmitter, Directive, Component} from "angular2/core";

@Component({
  selector: ['searchbar', '[searchbar]', '.searchbar'],
  templateUrl: 'build/components/searchbar/searchbar.html',
})
export class SearchbarComponent {
  constructor() {
    this.searchQuery = '';
    this.initializeItems();

    console.log("Initialised");
  }


  filterItems() {
    // do some filtering here
  }
}
{% endhighlight %}

The `ion-searchbar` will fail to load, it will not render on screen. You will just get an empty space where you expect it to be along with a lovely stack trace in the console

{% highlight text %}
browser_adapter.ts:83 EXCEPTION: No value accessor for '' in \
    [searchQuery in SearchbarComponent@0:15]
...
...
...
browser_adapter.ts:73 Error: No value accessor for ''
    at new BaseException (exceptions.ts:9)
    at _throwError (shared.ts:56)
    at Object.setUpControl (shared.ts:28)
    at NgModel.ngOnChanges (ng_model.ts:76)
    at AbstractChangeDetector.ChangeDetector_SearchbarComponent_0. \
        detectChangesInRecordsInternal (viewFactory_SearchbarComponent:45)
    at AbstractChangeDetector.detectChangesInRecords \
        (abstract_change_detector.ts:136)
    at AbstractChangeDetector.runDetectChanges (abstract_change_detector.ts:110)
    at AbstractChangeDetector._detectChangesInViewChildren \
        (abstract_change_detector.ts:237)
    at AbstractChangeDetector.runDetectChanges (abstract_change_detector.ts:115)
{% endhighlight %}

The reason this fails to load is because you **do not have the Ionic dependencies for the ion- component**.

Import them into the top of your JavaScript file and your component will render.

{% highlight javascript %}
import {EventEmitter, Directive, Component} from "angular2/core";
import {Searchbar, List, Item} from "ionic-angular";

@Component({
  selector: ['searchbar', '[searchbar]', '.searchbar'],
  templateUrl: 'build/components/searchbar/searchbar.html',
  directives: [Searchbar, List, Item]
})
export class SearchbarComponent {
  constructor() {
    this.searchQuery = '';
    this.initializeItems();

    console.log("Initialised");
  }

  filterItems() {
    // do some filtering here
  }
}
{% endhighlight %}

References:

- [http://stackoverflow.com/questions/34496514/ngmodel-no-value-accessor-for](http://stackoverflow.com/questions/34496514/ngmodel-no-value-accessor-for)
