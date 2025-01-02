---
author: "Marcelo Rodrigo"
categories:
  - Coisas da Vida
date: {{ .Date }}
lastmod: {{ .Date }}
description: '{{ replace .File.ContentBaseName "-" " " | title }}'
draft: true
url: '/{{ replace .File.ContentBaseName "-" " " | title }}'
keywords:
  - Bike
tags:
  - Bike
title: '{{ replace .File.ContentBaseName "-" " " | title }}'
type: post
---

# {{ replace .File.ContentBaseName "-" " " | title }}
