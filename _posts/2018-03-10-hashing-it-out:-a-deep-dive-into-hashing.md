---
title: "Hashing It Out: A Deep Dive into Cryptographic Hashing"
excerpt_separator: "<!--more-->"
categories:
  - basics
tags:
  - basics
  - hashing
header:
  overlay_image: /assets/images/url-encode.png
  overlay_filter: 0.5
  teaser: /assets/images/url-encode_reduced.png
  #og_image: /assets/Asymmetric-encryption.png
  #caption: "Photo from the series: [**Straying around**](/weekend_stories/2021/2021-03_Stray_around_3/)"
  actions:
    - label: "Read More"
      url: /weekend_stories/2021/2021-03_Stray_around_3/
excerpt: "URL encoding replaces special characters in URLs, ensuring proper navigation, web security, and making the internet accessible for all."
tagline: "Why do we need it and what would the internet look like without it."
---

Ever been overwhelmed by a food menu with too many choices? Yeah, that’s pretty much how the world of cryptographic hashing is. But no worries, my friend, I’m here to help you digest it all. By the end of our chat, you’ll be able to dish out hashing info like a pro. So grab a snack and let’s dive in!

<!--more-->

**What’s This Hashing Thing About?**

Hashing. It’s not what you do to your potatoes on a Sunday morning. In cryptography, it’s a way to take an input (or 'message') and return a fixed-size string of bytes, which is typically a 'digest'. What goes in can be any length - a line, a paragraph, or the entire "Game of Thrones" series (R.I.P. Daenerys). No matter how much data you feed it, the output, or hash, stays the same length.

The real magic trick here is that while it's a piece of cake to create a hash from an input, it's practically impossible to recreate the original input from the hash. Plus, any tiny change to the input creates a wildly different hash. 

**A Few Popular Hashing Algos**

Hashing algorithms, or hash functions, are the chefs behind the delicious hash we get. Let's take a look at a few crowd favorites.

1. **MD5** (Message Digest Algorithm 5): This used to be a superstar. It's fast and outputs a 128-bit hash value, usually rendered as a 32-character hexadecimal number. But alas! It fell from grace after vulnerabilities were discovered, allowing attackers to generate different inputs with the same hash. That’s like two completely different dishes tasting exactly the same. Uncanny, huh?

2. **SHA-1** (Secure Hash Algorithm 1): Producing a 160-bit hash value, this one’s a step up from MD5. But it suffered the same fate as MD5 when collisions were found. Now, it’s mostly chilling in the retirement zone.

3. **SHA-2**: This is more of a family of functions, and it's what we use when we want something more robust. It's like SHA-1's younger, stronger sibling, with fewer vulnerabilities. There's SHA-256 and SHA-512, which spit out 256-bit and 512-bit hashes respectively.

4. **SHA-3**: The newest member of the SHA family. It won the NIST hash function competition in 2012 and became the new federal standard in the U.S. in 2015. It's faster and more secure than SHA-2, like SHA-2 went to the gym and got ripped!

**Hashing Algorithms: Pros and Cons**

As with any tool, each hashing algorithm has its strengths and weaknesses. 

MD5 and SHA-1 are quick and easy to use, which makes them great for non-security functions like checksums. But their vulnerabilities to collision attacks make them risky choices for security-sensitive data.

SHA-2, while slower and more resource-intensive than MD5 and SHA-1, is currently much safer and is the industry standard for most cryptographic security systems today. It's like the sturdy minivan of hashing algorithms.

SHA-3, being the latest and greatest, offers the best security. But it's also the most resource-intensive. It's like the sports car of hashing - not always practical, but when you need the best, it's there.

**Hashing in Encryption and Digital Signatures**

Okay, now let’s see how this hashing business fits into the wider crypto scene. 

When you're encrypting data, hashing can help confirm whether the data has been tampered with

. You take your original data, hash it, then encrypt both the data and the hash. On the other end, they decrypt everything, recompute the hash on the data, and if the hashes match, bingo, the data is intact!

In digital signatures, hashing is key (pun intended!). You hash your data, then encrypt the hash with your private key. That encrypted hash is your digital signature. Anyone can take your data, hash it themselves, and decrypt your signature with your public key. If the hashes match, the data is authentic and hasn't been fiddled with. Voila!

**The Wrap-Up**

So there you have it, my friend - your guide to the tasty world of cryptographic hashing. Remember, all hash functions have their pros and cons, so you've gotta choose the right tool for the job. 

And even though they can look similar on the surface, hashing, encryption, and digital signatures all have different purposes. Just like breakfast hashes, omelets, and pancakes. Mmm, I think it's time for brunch...
