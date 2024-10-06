---
author: "Marcelo Rodrigo"
categories:
  - Desenvolvimento
date: 2024-10-06T21:22:31+02:00
description: 'Configuring HestiaCP to use PHP 8.3'
draft: false
keywords:
  - HestiaCP
  - PHP 8.3
  - PHP
tags:
  - HestiaCP
  - PHP
title: 'Configuring HestiaCP to use PHP 8.3'
type: post
---

# Configuring HestiaCP to use PHP 8.3

If you’re using `Hestia 1.8`, you might have noticed a bug where the `PHP 8.3` is not displayed correctly in the Hestia Web UI Settings. Don’t worry, this issue is set to be fixed in the next release.

In the meantime, you can manually add the version using your terminal.

## Adding PHP 8.3

First you must add the PHP 8.3 to your system.

```bash
sudo /usr/local/hestia/bin/v-add-web-php 8.3
```

## Enabling PHP 8.3 as default

To add the `PHP 8.3` to the `Enabled PHP Versions` - in the `Web Server configuration` - you must run this command:

```bash
sudo sed -i '/^\t"php-8.2",/a \\t"php-8.3",' /usr/local/hestia/web/edit/server/index.php
```

Thanks to `sahsanu` at the HestiaCP forum.

## Bonus: Remove unsupported PHP versions

PHP is a dynamic language that typically releases a new version every two years. As a result, older versions become unsupported, which can expose your server to security risks if they are still in use.

It's important to remove these legacy PHP versions. You can easily remove outdated PHP versions with the following command:

```bash
sudo /usr/local/hestia/bin/v-delete-web-php <version>
```
