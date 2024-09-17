---
author: Marcelo Rodrigo
categories:
- Desenvolvimento
date: "2014-10-01T08:59:14Z"
tags:
- java
- properties
title: How to sort properties in Java
url: /java-properties-file-sorted-by-key.html
---

Sometimes you have to deal with Properties files in Java. And sometimes you have to sort the entries based on the keys stored on the file, and you realized that is not so easy using default Properties class from java.util package.

This occurs because java.util.Properties extends java.util.Hashtable, which does not define a predictable sort order for keys or values.

For this situation, you can use the SortedProperties class to get entries sorted by key alphabetically.

{{< gist marcelorodrigo 7d1e2229393b21d4be07 >}}