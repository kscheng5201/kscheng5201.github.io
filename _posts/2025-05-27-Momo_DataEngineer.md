---
layout: post
title: Momo-DataEngineer
author: K.S. Cheng
status: completed
---

> **富邦媒體科技｜數據工程師**


1. ETL是Extract-Transform-Load的縮寫，請簡單敘述此三步驟定義。(5%)

    - Extract：
      
    - Transform：
      
    - Load：


2. 關於 OLTP 和 OLAP，下列敘述何者有誤？(複選) (5%)

    【  】1.OLTP是數據倉儲系統的主要應用

    【  】2.OLAP是傳統關係型數據庫的主要應用
   
    【  】3.銀行交易系統是屬於OLAP

    【  】4.OLTP強調數據分析、SQL執行時長


3. 請簡單敘述以下數據倉儲所包含的四個定義：(10%)

    - 面向主題：
    
    - 集成：
    
    - 隨時間變化：
    
    - 不可修改：


4. 請簡單敘述 DM（Data Mart，數據市集）和 DW（Data Warehouse，資料倉儲）的定義。(10%)

	DM：

	DW：


5. 請簡單敘述Kimball維度建模方法兩種表的定義。(20%)

    - 事實表：

    - 維度表：


6. 關於星型模型和雪花模型，下列敘述何者正確？(複選) (10%)

  【  】1.星型模型的特色是維度表和事實表直接相連
  
  【  】2.雪花模型的特色是有些維度不和事實表直接相連，而是透過其他維度和事實表相連
  
  【  】3.星型模型的優點是減少join次數，缺點是維度太多導致事實表查詢時效能較低
  
  【  】4.雪花模型的優點是減少冗於維度、提升事實表查詢效能，缺點是維度表間可能會較多 join 次數


7. 兩張大表(用戶:100萬筆資料，交易紀錄1000萬筆資料)，以下有 A、B 兩 SQL 查詢資料之語法，請回答哪一個SQL性能較好以及請敘述較不好的SQL其效能低下的可能原因：(20%)

    - user：用戶表，primary key 為 user_id
      
    - tx_log：交易紀錄表，primary key 為 tx_id, user_id
  

   ##### A
   ```
   select 
        user_id,
        user_name,
        count(1) as tx_count
   from (
        select 
            a.user_id,
            (select user_name from user b where a.user_id = b.user_id ) as user_name
        from 
            tx_log a 
        where 
            to_char(a.log_date, ‘yyyymm’) >= ‘201501’ and 
            to_char(a.log_date, ‘yyyymm’) <= ‘202512’  
        ) r 
    group by 
        user_id,
        user_name
   ```

   ##### B
    ```
    select 
        a.user_id
        max(b.user_name) as user_name,
        count(*) as tx_count
    from
        user b 
        left join tx_log a on b.user_id = a.user_id
    where 
        a.log_date >= to_date(‘20150101’ , ‘yyyymmdd’) and
        a.log_date < to_date(‘20160101’ , ‘yyyymmdd’)
    group by 
        a.user_id
    ```


8. RFM模型可以分析顧客的價值。主要會有最近消費天數(R)、消費頻率(F)、消費金額(M) 三個指標。
有張交易紀錄表 tx_log 紀錄以下內容，

   | tx_id | user_id  | log_date      | amount |
   |-------|----------|---------------|--------|
   | Tx1   | user-a   | 2023-01-01    | 100    | 
   | Tx2   | user-a   | 2023-01-02    | 150    | 
   | Tx3   | user-b   | 2023-05-01    | 700     | 
   | Tx3   | user-b   | 2023-05-03    | 300     | 

    - 每筆 tx_id 代表一次消費紀錄。
    - 消費頻率(F)：在此表示為每個使用者(user_id)的消費總次數。
    - 最近消費天數(R)：在此表示使用者離現在時間距離最近一次消費紀錄的差異天數，請使用 sql函式: `DATEDIFF(date1, date2)`。舉例: `DATEDIFF(now(), log_date)`。
    - 消費金額(M)：在此表示依使用者將 amount 欄位加總。

    請撰寫sql 計算出以每個user_id 統計之RFM 結果(結果表中每個user_id只會有一筆資料)，欄位如下: (20%)

   | user_id | r        | f             | m      |
   |---------|----------|---------------|--------|
