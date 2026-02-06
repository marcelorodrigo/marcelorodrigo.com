---
author: "Marcelo Rodrigo"
categories:
  - Tecnologia
date: 2026-01-19T20:06:40+02:00
description: 'Creating the FortyTen Hugo Theme'
draft: false
image: 'https://images.unsplash.com/photo-1461749280684-dccba630e2f6?q=80&w=2069&auto=format&fit=crop'
keywords:
  - Tecnologia
tags:
  - Hugo
title: 'Creating the FortyTen Hugo Theme'
type: post
url: '/creating-fortyten-hugo-theme'
---

# Creating the FortyTen Hugo Theme

After [migrating to Hugo last year](/migrating-from-wordpress-to-hugo/), I found myself wanting more control over how my blog looked and felt. The existing themes were great, but none of them truly matched what I had in mind. So I decided to build my own (yes, another one right?). The result is FortyTen, a theme I designed specifically for this website but made available for anyone who wants to use it.

## Why Build Your Own Theme

There is something deeply satisfying about creating something from scratch. You get to think about the reading experience from the perspective of your visitors rather than working around someone else's vision. And I wanted that, just for fun.

I spent years using WordPress themes that looked good but came with so much extra code I never needed. Building my own theme meant I could strip everything away and keep only what mattered. The result is cleaner, faster, and exactly what I wanted.

## What Makes FortyTen Different

FortyTen is built with Tailwind CSS 4, which makes styling much more intuitive than writing traditional CSS files. Every element has a purpose, and the code reflects that simplicity. I also included Alpine.js for the small interactive bits that make a site feel alive, like toggling dark mode and enabling search (yes, search without a backend, look at that mom).

The theme supports dark mode right out of the box. I wanted a reading experience that would be comfortable no matter what time of day you visit. The color scheme adjusts automatically based on your system preferences, or you can override it with a simple toggle.

I added a search feature that runs entirely in the browser. No external services, no tracking, no complicated setup. It just works and stays fast because the search index is generated at build time, thanks Hugo!

## Making It Available

I decided to release [FortyTen](https://fortyten.marcelorodrigo.com/) as an open source theme because I believe in giving back. Other developers might find it useful, or they might learn something from looking at how I structured it. Either way, putting it on GitHub means I have a backup of my work and a way to track improvements over time.

If you are thinking about building your own Hugo theme, I encourage you to go for it. Start small, focus on what you need, and expand from there. The process will teach you more about web development than any tutorial ever could. And when you are done, you will have something that is truly yours.

You can find FortyTen on [GitHub](https://github.com/marcelorodrigo/hugo-fortyten) if you want to use it for your own site or see how I built it, or visit the [theme website](https://fortyten.marcelorodrigo.com/) for documentation and demos.
