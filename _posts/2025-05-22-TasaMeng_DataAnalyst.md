---
layout: post
title: TasaMeng-DataAnalyst
author: K.S. Cheng
---

> **采盟｜資料數據分析師**

## 🧩 資料庫專業人員

1. 在考慮資料庫的需求時，除了使用者的需求外，資料庫的完整、安全等也要考慮。若某公司的總公司在台北，分公司在高雄，最適當的備份機制是哪一種？

   A. 線上備份（On-line backup）
   
   B. 離線備份（Off-line backup）
   
   C. 漸進備份（Incremental backup）

   D. 異地備份（Off-site backup）

   
3. 在客戶基本資料表（Customer）使用一段時間後，資料表中已有一大堆客戶資料。這時我們發現為了加快查詢速度，要對電話欄位（tel_no）建立索引。假設電話欄位只有一個，且電話號碼不會重複，我們執行 SQL 指令如下，則下列敘述何者正確？

   CREATE UNIQUE INDEX tel_no_idx ON Customer (tel_no);

   A. 一定可以成功建立索引

   B. 如果所有客戶都有電話號碼，且號碼不重複，就可以建立索引

   C. 所有客戶若都有電話號碼，則可以建立索引

   D. 一定無法建立索引

   
5. 請參閱附圖作答：

   A. 病患一定有醫生診治

   B. 一位醫師可以隸屬於不同的醫院

   C. 病患一定至某家醫院就診

   D. 醫院不一定會擁有病床
