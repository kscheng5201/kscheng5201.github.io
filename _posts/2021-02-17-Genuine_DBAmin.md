---
layout: post
title: Genuine-DatabaseAdmin
author: K.S. Cheng
---

> **捷元｜資料庫管理師**

## 資料表關聯圖

```
erDiagram

  productlines ||--o{ products : contains
  products ||--o{ orderdetails : contains
  orders ||--|{ orderdetails : contains
  customers ||--|{ orders : places
  customers ||--|{ payments : makes
  customers }o--|| employees : served_by
  employees ||--o{ employees : reports_to
  employees ||--o{ customers : manages
  employees ||--o{ offices : located_in
  offices ||--o{ employees : employs

  productlines {
    varchar productLine PK
    varchar textDescription
    text htmlDescription
    varbinary image
  }

  products {
    varchar productCode PK
    varchar productName
    varchar productLine FK
    varchar productScale
    varchar productVendor
    text productDescription
    smallint quantityInStock
    decimal buyPrice
    decimal MSRP
  }

  orderdetails {
    int orderNumber FK
    varchar productCode FK
    int quantityOrdered
    decimal priceEach
    smallint orderLineNumber
  }

  orders {
    int orderNumber PK
    date orderDate
    date requiredDate
    date shippedDate
    varchar status
    text comments
    int customerNumber FK
  }

  payments {
    int customerNumber FK
    varchar checkNumber PK
    date paymentDate
    decimal amount
  }

  customers {
    int customerNumber PK
    varchar customerName
    varchar contactLastName
    varchar contactFirstName
    varchar phone
    varchar addressLine1
    varchar addressLine2
    varchar city
    varchar state
    varchar postalCode
    varchar country
    int salesRepEmployeeNumber FK
    decimal creditLimit
  }

  employees {
    int employeeNumber PK
    varchar lastName
    varchar firstName
    varchar extension
    varchar email
    varchar officeCode FK
    int reportsTo FK
    varchar jobTitle
  }

  offices {
    varchar officeCode PK
    varchar city
    varchar phone
    varchar addressLine1
    varchar addressLine2
    varchar state
    varchar country
    varchar postalCode
    varchar territory
  }

```


## 資料表內容

### customers

| customerNumber | customerName             | contactLastName | contactFirstName | city       | state   | postalCode | country | salesRepEmployeeNumber | creditLimit |
|----------------|--------------------------|------------------|------------------|------------|---------|-------------|---------|-------------------------|--------------|
| 103            | Atelier graphique        | Schmitt          | Carine           | Nantes     | NULL    | 44000       | France  | 1370                    | 21000.00     |
| 112            | Signal Gift Stores       | King             | Jean             | Las Vegas  | NV      | 83030       | USA     | 1166                    | 71800.00     |
| 114            | Australian Collectors, Co.| Ferguson        | Peter            | Melbourne  | Victoria| 3004        | Australia| 1611                   | 117300.00    |
| 119            | La Rochelle Gifts        | Labrune          | Janine           | Nantes     | NULL    | 44000       | France  | 1370                    | 118200.00    |


### employees

| employeeNumber | lastName | firstName | extension | email                              | officeCode | reportsTo | jobTitle             |
|----------------|----------|-----------|-----------|------------------------------------|-------------|-----------|-----------------------|
| 1076           | Finelli  | Jeff      | x9273     | jfinelli@classicmodelcars.com      | 1           | 1002      | VP Marketing          |
| 1088           | Patterson| William   | x4871     | wpatterson@classicmodelcars.com    | 1           | 1143      | Sales Manager (APAC)  |
| 1102           | Bondur   | Gerard    | x5408     | gbondur@classicmodelcars.com       | 4           | 1056      | Sales Manager (EMEA)  |
| 1143           | Bow      | Anthony   | x5428     | abow@classicmodelcars.com          | 1           | 1056      | Sales Manager (NA)    |
| 1165           | Jennings | Leslie    | x3291     | ljennings@classicmodelcars.com     | 1           | 1143      | Sales Rep             |


### products

| productCode | productName                           | productLine   | productScale | productVendor          | productDescription                                                | quantityInStock | buyPrice | MSRP   |
|-------------|----------------------------------------|---------------|--------------|-------------------------|--------------------------------------------------------------------|------------------|----------|--------|
| S10_1678    | 1969 Harley Davidson Ultimate Chopper | Motorcycles   | 1:10         | Min Lin Diecast         | This replica features working kickstand, front suspe...          | 7933             | 48.81    | 95.70  |
| S10_1949    | 1952 Alpine Renault 1300              | Classic Cars  | 1:10         | Classic Metal Creations | Turnable front wheels; steering function; detailed int...         | 7305             | 98.58    | 214.30 |
| S10_2016    | 1996 Moto Guzzi 1100i                 | Motorcycles   | 1:10         | Highway 66 Mini Classics| Official Moto Guzzi logos and insignias, saddle bags...           | 6625             | 68.99    | 118.94 |
| S10_4698    | 2003 Harley-Davidson Eagle Drag Bike | Motorcycles   | 1:10         | Red Start Diecast       | Model features, official Harley Davidson logos and i...           | 5582             | 91.02    | 193.66 |


### payments

| customerNumber | checkNumber | paymentDate | amount   |
|----------------|-------------|-------------|----------|
| 103            | HQ336336    | 2004-10-19  | 6066.78  |
| 103            | JM555205    | 2003-06-05  | 14571.44 |
| 103            | OM314933    | 2004-12-18  | 1817.44  |
| 112            | BO864823    | 2004-12-17  | 14191.12 |



1. 顯示所有曾支付超過 $100,000 的客戶名稱。

2. 購買價格（buyPrice）高於所有產品平均水平購買價的結果，顯示產品代碼、產品名稱和數量。

3. 顯示職位名稱為 "Sales Rep" 的員工姓名和職位。

4. 我們需要從銷售哈雷戴維森摩托車獲得一些反饋。請為所有曾出售過 "Harley" 摩托車的員工獲取員工名字和電子郵件（重複的資料只留一筆）。

5. 我們希望顯示來自 France and the USA 的客戶。顯示客戶名稱、聯繫人姓名（例：John Lin）、國家。

6. 我們想深入瞭解客戶訂單歷史，請顯示客戶姓名，以及他們的初始訂單日期和最後的訂單日期。
