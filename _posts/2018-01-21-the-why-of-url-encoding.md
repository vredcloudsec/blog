---
title: "What is URL encoding?"
excerpt_separator: "<!--more-->"
categories:
  - basics
tags:
  - basics
  - encoding
header:
  overlay_image: /assets/images/url-encode.png
  overlay_filter: 0.5 
  #og_image: /assets/Asymmetric-encryption.png
  #caption: "Photo from the series: [**Straying around**](/weekend_stories/2021/2021-03_Stray_around_3/)"
  actions:
    - label: "Read More"
      url: /weekend_stories/2021/2021-03_Stray_around_3/
excerpt: "URL Encoding in the browser"
tagline: "Why do we need it and what would the internet look like without it."
---


Think of URL encoding as the secret sauce that keeps the internet running smoothly. You might have seen those "%20" or "%23" parts in a URL and wondered what they're all about. Well, they're pretty important. Without URL encoding, surfing the web would be like trying to navigate a ship through a storm—chaotic and full of errors.

**Why do we need URL encoding, anyway?**

Imagine you're typing a URL. You've got letters, numbers, maybe a few other characters like a dash (-) or an underscore (_). All these characters play nicely in a URL. But what happens if you want to include a space, or an ampersand (&), or a hash (#)? These characters cause trouble in a URL because they have special jobs. 

For instance, the "?" character in a URL is like a traffic cop, telling the server to get ready for some extra parameters coming its way. The "&" character is a multitasker, splitting up those parameters so the server can tell them apart. And the "#" character acts like a tour guide, pointing to a specific spot on a webpage. If these characters pop up elsewhere in the URL, it's like the server's getting instructions from a really bad GPS. Confusion city.

Plus, there are a bunch of other characters that aren't allowed in a URL because they could cause problems, be hard to read, or even be used for sneaky, underhanded stuff like hacking.

That's where URL encoding comes in. It swaps out the troublesome characters for a "%" sign followed by a couple of number-letter combos that represent the character in a URL-friendly format. Like a space turns into "%20", and a "#" turns into "%23".

**What if URL encoding took a vacation?**

Let's picture a world where URL encoding doesn't exist. It'd be like a Wild West of the web. Webpages might load up the wrong information, or maybe not load at all.

Let's say you're searching for "John & Jane's Wedding" on a photo site. Without URL encoding, the URL might look like this:

`https://www.photosite.com/search?query=John & Jane's Wedding`

The server might get confused by the "&" character and think "Jane's Wedding" is a totally different parameter. It'd be like asking for directions to the supermarket and instead being sent to the hardware store. Not helpful.

Even worse, without URL encoding, the web could be a whole lot less safe. Dodgy characters could use certain characters to mess with websites, causing all sorts of trouble like Cross-site Scripting (XSS) or SQL Injection. Thankfully, URL encoding puts a stop to that by making sure characters that could be used for mischief are kept under control.

And let's not forget about all the languages in the world that use non-ASCII characters. Without URL encoding, we wouldn't be able to reliably include these characters in URLs. So basically, URL encoding helps keep the internet accessible and usable for everyone, everywhere.

**Bottom line**

In the grand scheme of things, URL encoding is like a behind-the-scenes superhero of the internet. It makes sure URLs can be read properly by browsers and servers, helps people around the world use the web in their own language, and keeps our online experience safer. So next time you come across "%20" in a URL, give a nod to URL encoding, the unsung hero that keeps the digital world spinning.
