---
author: "Marcelo Rodrigo"
categories:
  - Coisas da Vida
date: 2024-09-09T20:06:40+02:00
description: 'Migrating From Wordpress to Hugo'
draft: false
keywords:
  - Tecnologia
tags:
  - Tecnologia
title: 'Migrating From Wordpress to Hugo'
type: post
url: '/migrating-from-wordpress-to-hugo'
---

# Migrating From Wordpress to Hugo
After 16 years of using WordPress, I migrated this website to Hugo. It comes with mixed feelings — I’ve had a lot of happiness using WordPress all these years, but it was time to move on.

## Rethinking my Wordpress usage
I started using WordPress around 2008, since I started this blog. At that time it was one of the most powerful tools to serve as a CMS. Over the years I wrote more than 200 posts, sharing my journey not only as a developer but also as a cyclist in my free time.

However, despite having a great audience, my blog’s updates became infrequent. I began to reconsider my need for WordPress. Sixteen years later, I realized I was no longer using many of the advanced features that WordPress offers.

Why use a tool designed to generate dynamic content when my content is mostly `static`?

## Hugo
Hugo is a static site generator, which means it does not need a database or heavy backend. It generates all the pages during build time. This makes the site faster and simpler to maintain. I can write all posts and pages using simple `Markdown`.

Another big reason I switched is speed. With Hugo, my website loads much faster because there’s no need to fetch data from database to generate the content. Not to mention that I could shutdown a RDS instance on AWS and save money.

In the end, Hugo gives me the simplicity, speed, and control I need without all the extra features I wasn’t using in WordPress.