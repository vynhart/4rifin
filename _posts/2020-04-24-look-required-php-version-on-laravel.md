---
layout: post
title:  "How to see what PHP version is required to run your laravel app"
categories: laravel
date:   2020-04-24 20:00:00 +0700
permalink: look-required-php-version-on-laravel/
---
How to see what laravel version is required to run your laravel app?
Follow this steps.

1. Open composer.json file in your laravel root directory
2. In "require" field, look for "php", you should see something similar to:
```
"php": ">=7.1.3"
```
 which means the PHP version required to run your laravel app is >=7.1.3

