+++
draft = false
date = 2021-08-19
title = "কিভাবে Hugo ভিত্তিক ওয়েবসাইটে Lazy Loading যোগ করবো?"
description = "How to active lazyloading Images on your Hugo based website."
slug = "lazy-loading-Images-in-hugo"
authors = ["মো. আবদুল্লাহ"]
tags = ["lazyloading"]
categories = ["Hugo"]
externalLink = ""
series = []
+++

ওয়েবে থাকা ছবিগুলি অন্য যেকোনো ধরনের রিসোর্সের চেয়ে বেশি ব্যান্ডউইথ গ্রহণ করে। কেন আমরা একটা ওয়েবসাইটের পুরো পাতাটা লোড করবো, যদি পুরো পাতাটা নাইবা পড়ি? 🤔 কেমন হয় যদি, পৃষ্ঠাতে যতটুকু দেখা যায়, ততটুকুই লোড হবে। স্ক্রল করে নিচে গেলে বাকিটুকু লোড হবে? এরকম ব্যাপারটিকেই বলে Lazy-Loading.  আপনি যদি [Hugo](https://gohugo.io/) স্ট্যাটিক সাইট জেনারেটর ব্যবহার করেন,তাহলে Lazy-Loading বাস্তবায়ন করা পানির মতোই সোজা। :open_mouth: সাধারন একাট HTML ফাইলে যোগ করার মতই সমান সহজ ।

তাহলে চলুন, শুরু করা যাক।

#### :one: Lazy-loading কাকে বলে?
[HubSpot](https://blog.hubspot.com/website/lazy-loading-eager-loading) এর মতে,
> Lazy-Loading হল লোড টাইম সর্বোচ্চ কমানোর জন্য ওয়েব পেজ দ্বারা ব্যবহৃত একটি কৌশল। Lazy-Loading চালু থাকলে, একটি ওয়েব পেজ প্রথমে শুধুমাত্র প্রয়োজনীয় সামগ্রী লোড করে, এবং ব্যবহারকারীর প্রয়োজন না হওয়া পর্যন্ত অবশিষ্ট পৃষ্ঠার সামগ্রী লোড করার জন্য অপেক্ষা করে।

![lazy-loading](/loazyloading.gif "Lazy-loading loads when you need")


#### :two: কেন ব্যবহার করবেন lazy-loading?
 Lazy-Loading একটি ওয়েব পেজ খুলতে সময় কমিয়ে দেয় কারণ ব্রাউজার শুধুমাত্র একবারে পৃষ্ঠার ততটুকুই লোড করে, যতটুকু স্ক্রিনে দেখা যাচ্ছে। স্ক্রল করে নিচে গেলে, তখন সেটা লোড করে।
 Lazy-Loading ব্যবহারে নিন্মোক্ত সুবিধাগুলো পাওয়া যায়।
 - প্রাথমিক লোড সময় হ্রাস করে।
 - ব্যান্ডউইথ বাঁচায়।
 - সিস্টেম রিসোর্স বাঁচায়।
 - ওয়েবসাইট টি দ্রুত লোড করে।
 - SEO তে উন্নতি করে।

আরো জানতে আগ্রহী? [web.dev](https://web.dev/lazy-loading/) থেকে বিস্তারিত জানতে পারেন।

#### :three: আপনার ওয়েবসাইটে Lazy-loading যোগ করুন।
প্রথমে আপনার Hugo ওয়েবসাইটে **/layouts/_default/_markup/render-image.html** এরকম একটা ফাইল তৈরি করুন। সেটাতে নিচের কোডটুকু লিখুন।

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
দারুন. :open_mouth: আমরা এটি করে ফেলেছি। ওয়েবসাইট টি বিল্ড করে পরিবর্তন টি দেখুন :sparkles:

আমি যাদের 👍 দিতে :heart:
* Lazy Loading ছবিটির জন্য [WordStream](https://www.wordstream.com/blog/ws/2020/12/08/lazy-loading-seo) কে।

উপকারী জ্ঞান ভাগাভাগিতে কার্পন্য নয়। শেয়ার করুন, বন্ধুদের সাথে। :heart_eyes:

এটাতে আর কি কি পরিবর্তন আনা যায়, সেটাও মন্তব্যের ঘরে জানাতে পারেন।
