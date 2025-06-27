---
layout: post
title: SinoPac-DataEngineer
author: K.S. Cheng
---


### 🧩 選擇題

1. 執行 SQL 查詢，何種指令可把兩段 SELECT 查詢結果（相同欄位）串連起來一併呈現？

   A. UNION
   B. With(NOLOCK)
   C. SELECT DISTINCT
   D. SELECT COUNT()

   
3. There is a table named Organ. Now we want to execute the following SQL statement and add a new column BRNO. Which commands should we use?
4. 有一個名為 Log 的資料表，它包含約五百萬筆資料列，每次搜尋都需要很久時間，以下何項可讓搜尋更有效率？
5. 以下哪項語法可從 CUST 資歷表取出前 10 筆資料列？
6. 以下 SQL 指令語法，空格內放入何項無誤？
7. There is a table named Organ. Now we want to find out the Organ which OrganID starts with BR. We'll execute the following SQL statement. Which is the most appropriate command to fill in the blank? SELECT OrganName From Organ WHERE ______ = 'BR'


### 🧩 基礎題


### 💡 Thought Process

- Use a hashmap to check for complements...

### ✅ Solution (Python)

```python
def twoSum(nums, target):
    lookup = {}
    for i, num in enumerate(nums):
        if target - num in lookup:
            return [lookup[target - num], i]
        lookup[num] = i
