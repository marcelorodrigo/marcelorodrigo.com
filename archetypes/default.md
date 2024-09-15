---
author: "Marcelo Rodrigo"
categories:
  - Coisas da Vida
date: {{ .Date }}
description: '{{ replace .File.ContentBaseName "-" " " | title }}'
draft: true
keywords:
  - Bike
tags:
  - Bike
title: '{{ replace .File.ContentBaseName "-" " " | title }}'
type: post
---

# {{ replace .File.ContentBaseName "-" " " | title }}