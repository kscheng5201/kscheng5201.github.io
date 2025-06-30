---
layout: post
title: SinoPac-DataEngineer
author: K.S. Cheng
---


## 🧩 一、選擇題

1. 執行 SQL 查詢，何種指令可把兩段 SELECT 查詢結果（相同欄位）串連起來一併呈現？
   
   A. UNION
   
   B. With(NOLOCK)

   C. SELECT DISTINCT
   
   D. SELECT COUNT()

   
2. There is a table named Organ. Now we want to execute the following SQL statement and add a new column BRNO. Which commands should we use?
  
   ________ TABLE Organ ________ BRNO varchar(10);
   
   A. ALTER, CREATE
   
   B. MODIFY, CREATE

   C. ALTER, ADD
   
   D. MODIFY, ADD

   
5. 有一個名為 Log 的資料表，它包含約五百萬筆資料列，每次搜尋都需要很久時間，以下何項可讓搜尋更有效率？

   A. 子查詢
   
   B. 觸發程序

   C. 資料指標
   
   D. 索引

   
7. 以下哪項語法可從 CUST 資歷表取出前 10 筆資料列？

   A. SELECT * FROM CUST WHERE rowcount <= 10

   B. SELECT TOP of 10 * FROM CUST

   C. SELECT * FROM CUST WHERE rowcount = 10

   D. SELECT TOP 10 * FROM CUST

   
9. 以下 SQL 指令語法，空格內放入何項無誤？

   SELECT ________ FROM Employee

   A. COLUMNS(*)

   B. SUM(Salary)

   C. TOTAL(Salary)

   D. COUNTS(Salary)

   
11. There is a table named Organ. Now we want to find out the Organ which OrganID starts with BR. We'll execute the following SQL statement. Which is the most appropriate command to fill in the blank?
    
    SELECT OrganName From Organ WHERE ______ = 'BR'

    A. SUBSTRING(OrganID, 2)

    B. SUBSTRING(OrganID, 2, 2)

    C. LEFT(OrganID, 2)

    D. CHARINDEX(OrganID, 2)

   
## 🧩 二、基礎題

   **📊 資料表 users 欄位內容如下**
   
   | id  | name   | gender    | age | hobby      |
   |-----|--------|-----------|-----|------------|
   | 1   | John   | male      | 23  | basketball |
   | 2   | Mary   | female    | 32  | baseball   |
   | 3   | Tom    | both      | 25  | sleep      |


1. 請試寫一段 SQL，從表格中取出所有的資料，並只顯示 name 欄位。

2. 請試寫一段 SQL，從 users 中選擇所有 gender 不等於 male 且 age 大於 24 歲的資料，並顯示所有欄位。

3. 請試寫一段 SQL，新增一筆到 users 中，資料值如下：

   | id  | name   | gender    | age | hobby      |
   |-----|--------|-----------|-----|------------|
   | 4   | Gary   | male      | 50  | coding     |

   
## 🧩 三、應用題

- 訂單資料表：SalesOrderDetail
  - 產品識別碼：ProductID
  - 訂單數量：OrderQty
  - 訂單金額：LineTotal

4. 使用 HAVING、AVG、SUM 等聚合函數，顯示產品識別碼、平均訂單數量，與訂單總計；從訂單資料表，依產品識別碼（ProductID）來分組，只顯示包括訂單總計超出 $1,000,000.00，且平均訂單數量小於 3 的產品群組，最後按照訂單總計由大到小排序。


## 🧩 四、綜合題

- 第一張表：Sarah 的收支統計表（Rev_Detail）
- 第二張表：Sarah 的銀行帳號管理（Acct_Main）
- 兩張表的唯一關聯在「帳號」

### 第一張表

   | 日期        | 類型   | 類型細項    | 金額（元） | 帳號        | 備註     |
   |------------|--------|-----------|-----------|------------|---------|
   | Txn_Date   | Type   | Sub_Type  | Amount    | Acct_Nbr   | Memo    |

-------------------------------------------------------------------------------

   | Txn_Date   | Type   | Sub_Type  | Amount    | Acct_Nbr   | Memo    |
   |------------|--------|-----------|-----------|------------|---------|
   | 20230401   | 支出    | 旅遊      | 10000      | 1234       | 銀行帳號 |
   | 20230402   | 支出    | 餐食      |   500      | 5678       |  信用卡  |
   | 20230403   | 收入    | 薪資      | 20000      | 2468       | 銀行帳號 |
   | 20230501   | 收入    | 稿費      |  1000      | 2468       | 銀行帳號 |
   | 20230503   | 收入    | 薪資      | 20000      | 2468       | 銀行帳號 |
   | 20230505   | 支出    | 餐食      |   200      |            |   現金   |
   | 20230507   | 支出    | 旅遊      |  5000      | 1234       | 銀行帳號 |
   | 20230510   | 支出    | 餐食      |  1500      | 5678       |  信用卡  |
   | 20230511   | 收入    | 稿費      |   300      | 2468       | 銀行帳號 |
   | 20230515   | 支出    | 餐食      |   100      | 1357       |  信用卡  |
   | 20230602   | 支出    | 餐食      |   150      | 8888       |  信用卡  |
   | 20230606   | 支出    | 餐食      |   800      | 8888       |  信用卡  |


### 第二張表

   | 帳號        | 交易銀行    |
   |------------|------------|
   | Acct_Nbr   | Txn_Bank   |

----------------------------------

   | Acct_Nbr   | Txn_Bank   |
   |------------|------------|
   | 1234       | 台銀        |
   | 1357       | 匯豐        |
   | 2468       | 永豐        |
   | 5678       | 兆豐        |
   | 8888       | 一銀        |


5. 計算出各種類型細項的花費，並依總金額由大到小排序。列示欄位包含：類型細項、金額總計。
6. 使用 JOIN 將這兩張表串聯在一起，結合成一張總表，並按照日期排序。
7. 使用 LIKE 或 IN，列出 Sarah 在 5 月份的支出交易明細：金額大於 1,200 元，且交易銀行為永豐或者兆豐、匯豐的資料。列示欄位包含：日期、交易銀行、類型細項、金額。 


## 🧩 五、問答題
- 四份資料表，欄位內容如下：

A. EMP（員工主檔：理專編號、理專姓名、隸屬分行名稱）

   | DMPID   | EMPNAME | BRNAME    | 
   |---------|---------|-----------|
   | A11111  | 王理專   | 台北分行    |
   | A22222  | 黃理專   | 高雄分行    |
   | A33333  | 陳理專   | 台中分行    |
   | A44444  | 王理專   | 台北分行    |


B. CUST（客戶主檔：客戶身份證號、客戶姓名、理專編號、年紀）

   | CUSTOMER_ID  | CUSTOMER_NAME | EMPID    | AGE | 
   |--------------|---------------|----------|-----|
   | A123123123   | MARK          | A11111   | 30  | 
   | A220123321   | BETTY         | A22222   | 10  | 
   | A111999999   | DAVID         | A33333   | 40  | 
   | H200721777   | RUBY          | A11111   | 55  | 

   
C. ACCOUNT（存款主檔：客戶身份證號、帳號、金額、利率％、幣別、分行別）

   | CUSTOMER_ID  | ACCOUNT_NO        | AMOUNT  | INTDEGREE | CURRENCY   | BRNO    |
   |--------------|-------------------|---------|-----------|------------|---------|
   | A123123123   | 00100400513433    | 10000   | 2.45000   | USD        | 001     |
   | A123123123   | 00100400513433    | 10000   | 2.45000   | USD        | 001     |
   | A123123123   | 00100400513433    | 10000   | 2.45000   | USD        | 001     |
   | A123123123   | 00100400513433    | 10000   | 2.45000   | USD        | 001     |
   | A123123123   | 00100400513433    | 10000   | 2.45000   | USD        | 001     |
   | A123123123   | 00100400513433    | 10000   | 2.45000   | USD        | 001     |
   | A123123123   | 00100400513433    | 10000   | 2.45000   | USD        | 001     |
   | A123123123   | 00100400513433    | 10000   | 2.45000   | USD        | 001     |
   | A123123123   | 00100400513433    | 10000   | 2.45000   | USD        | 001     |
   | A123123123   | 00100400513433    | 10000   | 2.45000   | USD        | 001     |
   | A123123123   | 00100400513433    | 10000   | 2.45000   | USD        | 001     |
   | A123123123   | 00100400513433    | 10000   | 2.45000   | USD        | 001     |

D. RATE（利率主檔：販賣幣別、基礎幣別、匯率）

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
