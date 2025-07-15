---
layout: post
title: Wipro_DataEngineerAnalyst
author: K.S. Cheng
status: completed
---

> **Wipro｜資料工程師／資料分析師**


## 🧩 Leetcode 262. Trips and Users

Table: `Trips`

| Column Name | Type     |
|-------------|----------|
| id          | int      |
| client_id   | int      |
| driver_id   | int      |
| city_id     | int      |
| status      | enum     |
| request_at  | varchar  |     


id is the primary key (column with unique values) for this table.
The table holds all taxi trips. Each trip has a unique id, while client_id and driver_id are foreign keys to the users_id at the Users table.
Status is an ENUM (category) type of ('completed', 'cancelled_by_driver', 'cancelled_by_client').


Table: `Users`

| Column Name | Type     |
|-------------|----------|
| users_id    | int      |
| banned      | enum     |
| role        | enum     |

users_id is the primary key (column with unique values) for this table.
The table holds all users. Each user has a unique users_id, and role is an ENUM type of ('client', 'driver', 'partner').
banned is an ENUM (category) type of ('Yes', 'No').


- The cancellation rate is computed by dividing the number of canceled (by client or driver) requests with unbanned users by the total number of requests with unbanned users on that day.

- Write a solution to find the cancellation rate of requests with unbanned users (both client and driver must not be banned) each day between "2013-10-01" and "2013-10-03" with at least one trip. Round Cancellation Rate to two decimal points.

- Return the result table in any order.

- The result format is in the following example.



### Input: 

#### Trips table:


| id | client_id | driver_id | city_id | status              | request_at |
|----|-----------|-----------|---------|---------------------|------------|
| 1  | 1         | 10        | 1       | completed           | 2013-10-01 |
| 2  | 2         | 11        | 1       | cancelled_by_driver | 2013-10-01 |
| 3  | 3         | 12        | 6       | completed           | 2013-10-01 |
| 4  | 4         | 13        | 6       | cancelled_by_client | 2013-10-01 |
| 5  | 1         | 10        | 1       | completed           | 2013-10-02 |
| 6  | 2         | 11        | 6       | completed           | 2013-10-02 |
| 7  | 3         | 12        | 6       | completed           | 2013-10-02 |
| 8  | 2         | 12        | 12      | completed           | 2013-10-03 |
| 9  | 3         | 10        | 12      | completed           | 2013-10-03 |
| 10 | 4         | 13        | 12      | cancelled_by_driver | 2013-10-03 |



#### Users table:

| users_id | banned | role   |
|----------|--------|--------|
| 1        | No     | client |
| 2        | Yes    | client |
| 3        | No     | client |
| 4        | No     | client |
| 10       | No     | driver |
| 11       | No     | driver |
| 12       | No     | driver |
| 13       | No     | driver |


#### Output: 

| Day        | Cancellation Rate |
|------------|-------------------|
| 2013-10-01 | 0.33              |
| 2013-10-02 | 0.00              |
| 2013-10-03 | 0.50              |


### Explanation: 
On 2013-10-01:
  - There were 4 requests in total, 2 of which were canceled.
  - However, the request with Id=2 was made by a banned client (User_Id=2), so it is ignored in the calculation.
  - Hence there are 3 unbanned requests in total, 1 of which was canceled.
  - The Cancellation Rate is (1 / 3) = 0.33

On 2013-10-02:
  - There were 3 requests in total, 0 of which were canceled.
  - The request with Id=6 was made by a banned client, so it is ignored.
  - Hence there are 2 unbanned requests in total, 0 of which were canceled.
  - The Cancellation Rate is (0 / 2) = 0.00

On 2013-10-03:
  - There were 3 requests in total, 1 of which was canceled.
  - The request with Id=8 was made by a banned client, so it is ignored.
  - Hence there are 2 unbanned request in total, 1 of which were canceled.
  - The Cancellation Rate is (1 / 2) = 0.50



## 🧩 Prescreen Questions

  - Which data visualization tools are you proficient in? Please describe your experience with each.
    
  - Can you provide examples of dashboards or reports you've created, and describe the insights they provided?

  - Describe your experience with data manipulation using spreadsheet software like Google Sheets. Can you give an example of a complex data transformation you've performed?

  - What is your experience level with SQL? Can you describe a scenario where you used SQL to extract or transform data?

  - Tell me about the most complex project you were part of that went poorly. (Follow-ups: What was your role? What went wrong? What unplanned problems arose and how did you deal with them? What lessons did you learn? What was one thing you did to make it more successful or get it back on track?)

  - Tell me about a project for which you lacked key information or direction but needed to make progress. (Follow-ups: In order to proceed, what resources did you consult? When consulting those resources, how did you determine which data points were most important? Did you encounter any obstacles other than lack of information and how did you overcome them? What was the eventual outcome? If faced with the same situation in the future, what would you do differently?)
