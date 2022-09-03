+++
draft = false
date = "2021-08-22"
title = "কিভাবে আগে থেকেই ইনস্টল করা ফেসবুক-কে সম্পূর্ণরূপে অপসারণ করবেন?"
description = ""
slug = "remove-facebook-completely"
authors = ["মো. আবদুল্লাহ"]
tags = ["নিরাপত্তা","গোপনীয়তা","ফেসবুক"]
categories = ["ভালো থাকুন"]
externalLink = ""
series = []
+++

### :one: Android Debug Bridge (ADB) সফটওয়্যারটি ডাউনলোড করুন।
- প্রথমে আপনার কম্পিউটারে [ADB Tool](https://developer.android.com/studio/releases/platform-tools#downloads) টি ডাউনলোড করুন।
- ডাউনলোড হয়ে গেলে সেটাকে UnZip/Extract করুন।

{{< notice tip >}}
Unzip/Extract করার জন্য [7zip](https://www.7-zip.org/) ব্যবহার করতে পারেন।
{{< /notice >}}

### :two: আপনার এন্ড্রোয়েড ফোনে **ডেভেলপার মোড** চালু করুন।
- **সেটিংস** এ যান
- **ফোন পরিচিতি** তে যান
- **সফটওয়্যারের তথ্য** তে যান
- **বিল্ড নম্বর** এ ৭ বার দ্রুত টোকা দিন

আবারো সেটিংসে যান। এবার দেখুন **ফোন পরিচিতির** নিচেই রয়েছে **ডেভেলপার অপশন।** সেখান থেকে
- **চালু** বোতামটি চেপে **ডেভেলপার মোড** চালু করে নিন।
- **USB ডিবাগিং** টাও চালু করে নিন।

বুঝতে অসুবিধা হলে [এখানে](https://www.samsung.com/uk/support/mobile-devices/how-do-i-turn-on-the-developer-options-menu-on-my-samsung-galaxy-device/) দেখতে পারেন।

{{< notice note >}}
আমি আমার Samsung M02s অনুযায়ী, **ডেভেলপার মোড** চালুর ব্যপারটা দেখিয়েছি। আপনার ফোনে সেটা কিছুটা ভিন্ন হতে পারে।
{{< /notice >}}


### :three: কম্পিউটারের সাথে ফোনটি সংযুক্ত করুন।

{{< notice info >}}
এটি একটি প্রতীকি ছবি।

![আপনার কম্পিউটারের সাথে ফোনটি সংযুক্ত করুন।](/usb-pc.jpg "কম্পিউটারের সাথে ফোনের সংযোগ করণ")
{{< /notice >}}

### :four: CMD চালু করুন।
যেখানে ADB Tool টি UnZip/Extract করেছিলেন, সেই ফোল্ডারের এড্রেসবারে গিয়ে cmd লিখুন ও এন্টার চাপুন।

{{< notice example >}}
![ফোল্ডারের এড্রেসবারে গিয়ে cmd লিখুন ও এন্টার চাপুন।](/deletefacebookCMD.png "উইন্ডোজ পিসির ফোল্ডারের এড্রেসবারে গিয়ে cmd লিখুন ও এন্টার চাপুন।")
{{< /notice >}}


### :five: CMD তে নিচের কমান্ডগুলো চালান।
ঠিকঠাকমতো, ADB চালু হলে পর্যায়ক্রমে নিচের কমান্ডগুলো চালান।

আপনার ফোন কম্পিউটারের সাথে সংযোগ হলো কি না?
>adb devices

ADB শেল চালু করুন
>adb shell


যে সমস্ত প্যাকেজের নামের মধ্যে facebook কথাটি আছে, সেগুলো বের করুন
>pm list packages | grep 'facebook'


সাধারনত এই কয়টি প্যাকেজ থাকতে পারে।
- com.facebook.katana
- com.facebook.system
- com.facebook.services
- com.facebook.appmanager

এবার সবগুলোকে নিচের মতো কমান্ড দিয়ে কেটে দিন।
> pm uninstall -k --user 0 com.facebook.services

>pm uninstall -k --user 0 com.facebook.system

>pm uninstall -k --user 0 com.facebook.system

>pm uninstall -k --user 0 com.facebook.appmanager

{{< notice example >}}
আমার ফোনে মাত্র দুটি প্যাকেজ দেখা যাচ্ছে। কারন, এই টিউটোরিয়াল তৈরির আগেই আমি আমার ফোনে যাচাই করে দেখেছিলাম। তাই, এখানে সবকয়টা প্যাকেজ দেখা যাচ্ছে না।
মোদ্দাকথা, facebook লিখে সার্চ দিলে যে প্যাকেজগুলো আসবে, সেগুলো এই কমান্ডের মত করে আনইনস্টল করে দিতে হবে।
![](/facebookcmd.png "Command for deleting facebook completely from android phone")
{{< /notice >}}

আলহামদুলিল্লাহ। আমরা ফেসবুক কে আমাদের ফোন থেকে চিরতরে বিদায় দিতে পেরেছি। যাচাই করতে Play Store এ ফেসবুক লিখে সার্চ দিন

![Facebook in PlayStore](/facebook-play-store.jpg "প্লে স্টোরে Install করতে বলা হচ্ছে মানেই, সেটা এখন আর আপনার ফোন নাই")

{{< notice warning >}}
এই টিউটোরিয়ালে যা দেখানো হয়েছে, সেটা অভিজ্ঞ ব্যবহারকারীদের জন্য। ভুলবশত সিস্টেমের অন্য কোন অ্যাপ ডিলেট করে ফেললে, আপনার ফোন নষ্ট হতে পারে। সেক্ষেত্রে আমি কোন ক্রমেই দ্বায়ী নই।
{{< /notice >}}

{{< notice info >}}
ভুলবশত কোন সিস্টেম অ্যাপ ডিলেট করে ফেললে নিকটস্থ সার্ভিস সেন্টারে গিয়ে আপনার ফোনে অপারেটিং সিস্টেমটি পুনরায় ইনস্টল করুন।
{{< /notice >}}
