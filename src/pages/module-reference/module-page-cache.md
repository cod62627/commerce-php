---
title: PageCache
description: N/A
---

The PageCache module provides functionality of caching full pages content in Magento application. An administrator may switch between built-in caching and Varnish caching. Built-in caching is default and ready to use without the need of any external tools.
Requests and responses are managed by PageCache plugin. It loads data from cache and returns a response. If data is not present in cache, it passes the request to Magento and waits for the response. Response is then saved in cache.
Blocks can be set as private blocks by setting the property '_isScopePrivate' to true. These blocks contain personalized information and are not cached in the server. These blocks are being rendered using AJAX call after the page is loaded. Contents are cached in browser instead.
Blocks can also be set as non-cacheable by setting the 'cacheable' attribute in layout XML files. For example `<block class="Block\Class" name="blockname" cacheable="false" />`. Pages containing such blocks are not cached.

<InlineAlert slots="text" />
The version of this module is 100.4.8.
