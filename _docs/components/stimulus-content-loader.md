---
layout: component
title: Content Loader
parent: Available controllers
package: content-loader
netlify_id: bc6c7113-e3e7-4d1f-9508-4b631eea2e70
---

A Stimulus controller to asynchronously load HTML from an url.

## Video Tutorial

[Dave Kimura](https://twitter.com/kobaltz) from [Drifting Ruby](https://www.driftingruby.com/) has released a presentation video on how to use this package with a real life example.

👉 Take a look: [Deferred Content Loading](https://www.driftingruby.com/episodes/deferred-content-loading)

{% include youtube.html id="kZircHj1KI0" %}

## Installation

```bash
$ yarn add stimulus-content-loader
```

And use it in your JS file:
```js
import { Application } from "stimulus"
import ContentLoader from "stimulus-content-loader"

const application = Application.start()
application.register("content-loader", ContentLoader)
```

{% include demo.md %}

## Usage

In your controller:
```ruby
class PostsController < ApplicationController
  def comments
    render partial: 'posts/comments', locals: { comments: @post.comments }
  end
end
```

In your routes:
```ruby
Rails.application.routes.draw do
ressources
  get :comments, to: 'posts#comments'
end
```

In your view:
```html
<div
  data-controller="content-loader"
  data-content-loader-url-value="<%= comments_path %>"
>
  <i class="fas fa-spinner fa-spin"></i> Loading comments...

  This content will be replaced by the content of the `posts/comments` partial generated by Rails.
</div>

<div
  data-controller="content-loader"
  data-content-loader-url-value="<%= comments_path %>"
  data-content-loader-refresh-interval-value="5000"
>
  This content will be reloaded every 5 seconds.
</div>

<div
  data-controller="content-loader"
  data-content-loader-url-value="/message.html"
>
  This content will be replaced by the content of the `/message.html` page in your public folder.
</div>

<div
  data-controller="content-loader"
  data-content-loader-url-value="/message.html"
  data-content-loader-lazy-loading-value=""
>
  This content will be replaced only when the element become visible thanks to Intersection Observers.
</div>

<div
  data-controller="content-loader"
  data-content-loader-url-value="/message.html"
  data-content-loader-lazy-loading-value=""
  data-content-loader-lazy-loading-root-margin-value="30px"
  data-content-loader-lazy-loading-threshold-value="0.4"
>
  You can customize the Intersection Observer options.
</div>

<div
  data-controller="content-loader"
  data-content-loader-url-value="/message.html"
  data-content-loader-lazy-loading-value=""
  data-content-loader-refresh-interval-value="5000"
>
  You can combine lazy loading and refresh interval. The timer will start only after the first fetch.
</div>
```

## 🛠 Configuration

| Attribute | Default | Description | Optional |
| --------- | ------- | ----------- | -------- |
| `data-content-loader-url-value` | `undefined` | URL to fetch the content. | ❌ |
| `data-content-loader-refresh-interval-value` | `undefined` | Interval in milliseconds to reload content. | ✅ |
| `data-content-loader-lazy-loading-value` | `undefined` | Fetch content when element is visible. | ✅ |
| `data-content-loader-lazy-loading-root-margin-value` | `0px` | rootMargin option for Intersection Observer. | ✅ |
| `data-content-loader-lazy-loading-threshold-value` | `0` | threshold option for Intersection Observer. | ✅ |


## 🎛 Extending Controller

{% capture content %}
```js
import Reveal from "stimulus-reveal-controller"

export default class extends Reveal {
  connect() {
    super.connect()
    console.log("Do what you want here.")
  }
}
```

{% endcapture %}

{% include extending_controller.md content=content %}

## Credits

This controller is inspired by the [official Stimulus example](https://stimulusjs.org/handbook/working-with-external-resources).