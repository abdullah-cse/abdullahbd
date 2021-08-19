+++
draft = false
date = 2021-08-19
title = "Lazy-loading Images on Hugo based Website"
description = "If you are using Hugo static site generator, the implementation of it is equally simple as adding it to an HTML file and you don’t have a good reason not to do so."
slug = "lazy-loading-Images-in-hugo"
authors = ["MD. ABDULLAH"]
tags = ["lazyloading"]
categories = ["Hugo"]
externalLink = ""
series = []
+++

Images on the web take up more bandwidth than any other type of resources. Why do we have to load them all even if we are never going to scroll far enough to see them? If you are using Hugo static site generator, the implementation of it is equally simple as adding it to an HTML file and you don’t have a good reason not to do so.

#### :one: What is Lazy-loading?
By [HubSpot](https://blog.hubspot.com/website/lazy-loading-eager-loading)
>Lazy loading is a technique used by web pages to optimize load time. With lazy loading, a web page loads only required content at first, and waits to load any remaining page content until the user needs it.

![lazy-loading](/loazyloading.gif "Lazy-loading loads when you need")


#### :two: Why lazy-loading?
 Lazy loading reduces the time it takes for a web page to open because the browser only loads a fraction of the content on the page at a time.
 - Reduces initial load time
 - Bandwidth conservation
 - System resource conservation

Want to know more? Get Motivation from [web.dev](https://web.dev/lazy-loading/)

#### :three: Add Lazy-loading Images in your Hugo website!
Create a file in **/layouts/_default/_markup/render-image.html** like this.

```html
<!-- layouts/_default/_markup/render-image.html -->
{{ $img := imageConfig (add "/static" (.Destination | safeURL)) }}

<img
  src="{{ .Destination | safeURL }}"
  alt="{{ .Text }}"
  loading="lazy"
  width="{{ $img.Width }}"
  height="{{ $img.Height }}"
/>
```
Awesome. :open_mouth: We did it. Render and inspect the Changes :sparkles:

I :heart: to Thanks 👍
* [WordStream](https://www.wordstream.com/blog/ws/2020/12/08/lazy-loading-seo) for the Lazy Loading GIF

Sharing is Caring. :heart_eyes:
