---
layout: post
title: SomeCodeForZotero
date: 2023-10-07
description:  # Add post description (optional)
img: i-rest.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Zotero,js]
---

# Zotero code

- **即时删除rss**
    - ```
        `ZoteroPane.getSelectedItems()[0].eraseTx({ skipEditCheck: true })`
    ```
        

- **即时删除所有rss**
    - ```
        var feeds = ZoteroPane.getSelectedItems();
        for (let feed of feeds){
        await feed.eraseTx({ skipEditCheck: true });
        }
    ```
        

- **即使取消订阅所有RSS**
    - ```
        var feeds = Zotero.Feeds.getAll();
        for (let feed of feeds){
            await feed.eraseTx({ skipEditCheck: true });
        }
    ```



