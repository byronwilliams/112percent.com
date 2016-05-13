---
author: ""
date: "2016-02-05T08:44:25Z"
description: ""
tags: ["angular2", "angular1", "datapipe"]
title: "angular2 datepipe"
type: "post"
location: On a train to Wigan
---

In one of my Angular2 services I need to send date in a specific format to a JSON endpoint.

I felt that I shouldn't have to reinvent the wheel and I could just do what I did in Angular1.

{% highlight javascript %}
let formattedDate = $filter(new Date(), "date:'yyyy-MM-dd'");
{% endhighlight %}

Filters are now called Pipes in Angular2. You can easily import them from the `common` module.

{% highlight javascript %}
let dp = new DatePipe();
return dp.transform(new Date(), ["yyyy-MM-dd"])
{% endhighlight %}

After a lot of playing around I came up with the following code for my service

{% highlight typescript %}
import {Http} from 'angular2/http';
import {DatePipe} from 'angular2/common';

@Injectable()
export class MyService {
    constructor(private _http: Http) {}

    public GetLatestPosts(): any {
        let since = this._formatDateForSQL(new Date());
        return this._http.get(`myurl?since=${since}`);
    }

    private formatDateForSQL(date: Date): string {
        let dp = new DatePipe();
        return dp.transform(date, ["yyyy-MM-dd"])
    }
}
{% endhighlight %}
