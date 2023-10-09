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
        ZoteroPane.getSelectedItems()[0].eraseTx({ skipEditCheck: true })`
    ```


- **即时删除所有rss**
    - ```
        var feeds = ZoteroPane.getSelectedItems();
        for (let feed of feeds){
        await feed.eraseTx({ skipEditCheck: true });
        }
    ```


- **即时取消订阅所有RSS**
    - ```
        var feeds = Zotero.Feeds.getAll();
        for (let feed of feeds){
            await feed.eraseTx({ skipEditCheck: true });
        }
    ```
    

- **选定项目更新网页快照**
    - 参考资料
        - https://gist.github.com/jryans/f2631cf3b2c500817cdf79a791209bca
        - https://forums.zotero.org/discussion/85656/script-to-convert-old-web-snapshots-to-new-format
    - ```
        var items = Zotero.getActiveZoteroPane().getSelectedItems();
        var itemIdLists = [];
        for (let item of items){
            var itemId = item.id;
            itemIdLists.push(itemId);
        }
        var items = await Zotero.Items.getAsync(itemIdLists);
        for (let item of items) {
            var libraryID = item.libraryID;
            var parentItemID = item.id;
            var url = item.getField("url");
            try {
                var oldAttachmentID = item.getAttachments();
                for (let att of oldAttachmentID){
                    await Zotero.Items.trashTx(att); 
                };
                await Zotero.Attachments.importFromURL({
                    libraryID,
                    parentItemID,
                    url,
                    title: "Snapshot",
                    contentType: "text/html",
                });
                Zotero.debug(`Snapshot done: ${item.getField('title')}`)
            } catch (e) {
                Zotero.debug(e);
            }
        }
    ```








