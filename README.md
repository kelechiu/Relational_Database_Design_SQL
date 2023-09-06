
#   Kangaroo Relational Database Design

## 1.  Introduction
Kangaroo is an online delivery company that wishes to develop a Relational Database Management System (RDBMS) to support its’ business processes. 

The aim of this section is to design an effective Entity Relationship (ER) diagram for Kangaroo’s database and implement it to support their business processes.

## ER Diagram using Crows Foot Notation

<img width="429" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/1a3ec595-8fb5-4dc1-acc3-4739e0dca229">

## 2.  Cardinality Relationships Between Entities

### 2.1.  Customer and Orders
The customer entity has a one-to-many relationship with orders which allows a customer to place multiple orders, but an order can only be placed by one customer.

 ![image](https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/4d5d89a9-887c-477d-81cc-428c543bc8fa)

### 2.2.  Orders and Items
The order entity has a many-to-many relationship with items because a single order can contain multiple items and an item can be included in multiple orders.

 ![image](https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/f6baab28-95e0-47c3-9c0e-217fc6b03497)

### 2.3.  Orders and Restaurants
The order entity has many-to-one relationship because multiple orders can be associated with a single restaurant, however, a single order is placed at a single restaurant.
 
 ![image](https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/c909349a-c725-49af-ba6b-50248a6f780b)

### 2.4.  Restaurants and Driver
The restaurant entity has a one-to-many relationship because each restaurant employs many drivers, but each driver is associated with one restaurant only.

 ![image](https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/e62e6b1d-3613-4773-b050-0d178a2a5f7e)

### 2.5.  Drivers and Orders
The driver entity has a one-to-many relationship with orders, because each driver can deliver multiple orders, but one order can only be delivered by a single driver.

 ![image](https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/339a9171-1e96-4421-9697-7cd117750e20)

### 2.6.  Driver and Vehicle
The driver entity has a one-to-one relationship with vehicle because each driver is assigned one motorcycle for the duration of their contract.

![image](https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/4cd121c9-299f-4382-b0e6-d472b23fe9da)

### 2.7.  Manager and Driver
The manager entity has a many-to-one relationship with driver because one manager can manage multiple drivers, but each driver has only one manager.

 ![image](https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/72e92391-a4ba-4dc2-a5a4-9788ac43d39c)

### 2.8.  Driver and Driver’s License
The driver entity has a one-to-one relationship with driver’s license because each driver has one driver’s license, and each license belongs exclusively to that driver.

 ![image](https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/863ed756-0af9-47b3-acf2-32e3941951d1)

### 2.9.  Driver and Payroll
The driver entity has a one-to-many relationship with payroll, because each driver can have multiple payroll records, but each payroll is issued to a single driver.

![image](https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/2e550d69-39d5-4c23-a816-d984af1ca0ba)

## 3. 	SQL Implementation of Database Design
I created a company database called Kangaroo to store the tables below.

<img width="172" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/429c15dd-0df0-4355-9a5c-e16ffb7e996d">

### 3.1.  Create ‘Customers’ Table

<img width="200" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/c934583b-d526-4362-9de2-c74f7ffc3b44">

####  Data Types and Constraints
* The Primary Key is Customer_ID because it uniquely identifies each customer.
* I assigned VARCHAR to names and emails because the length of the characters can vary.
* The numbers in brackets indicate the maximum length of characters.
* The NOT NULL constraint indicates that certain columns like customer_ID and phone numbers must not be left empty.
* The CHECK CONSTRAINT specifies that all entries in the email column must contain the ‘@’ symbol.

####  Table Population
``` mysql
-- Populate Customers Table
INSERT INTO Customers VALUES
    ('C-01', 'Kelechi', 'Uzoukwu', 'kelechi.u@yahoo.com', '07234567890'),
    ('C-02', 'Emily', 'Johnson', 'emily.j@yahoo.com', '07987654321'),
    ('C-03', 'Ada', 'Brown', 'ada.b@yahoo.com', '07087654391'),
    ('C-04', 'Amaka', 'Okafor', 'amaka.o@yahoo.com', '07987874321'),
    ('C-05', 'Imelda', 'Obi', 'imelda.o@gmail.com', '07787698321'),
    ('C-06', 'Ugo', 'Uzoka', 'ugo.uzoka@yahoo.com', '07547654321'),
    ('C-07', 'Hillary', 'White', 'hillary.w@gmail.com', '07932654321'),
    ('C-08', 'John', 'Paul', 'john.p@yahoo.com', '07298354321'),
    ('C-09', 'Ken','Jones', 'ken.j@yahoo.com', '07987609321'),
    ('C-10', 'Chinwe', 'Ojo', 'chinwe.o@yahoo.com', '07987621121');

  ```
<img width="235" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/dd999aa3-730a-487b-9c52-54601429888a">


### 3.2.  Create ‘Restaurants’ Table

<img width="192" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/6dd15e29-dc41-46f4-b6de-546f4c90fe40">

#### Data Types and Constraints
* The Primary Key is Restaurant_ID because it uniquely identifies each restaurant.
* I assigned VARCHAR to the name and address because the length of the characters can vary.
* NOT NULL constraint specifies that each restaurant must be associated with a Restaurant_ID and name.

``` mysql

-- Populate Restaurants Table
INSERT INTO Restaurants VALUES
    ('R-201', 'Pizza Hut', '13 Main Street'),
    ('R-202', 'McDonalds', '45 Elm Street'),
    ('R-203', 'Wendys', '20 Eastbrook St'),
    ('R-204', 'Burger King', '2 Scarborough Av'),
    ('R-205', 'Dominos', '34 Baker Street'),
    ('R-206', 'Meaty Pub', '56 Oncu Close'),
    ('R-207', 'Green Kitchen', '9 Trinity Avenue'),
    ('R-208', 'Dixy Chicken', '80 Edmonton St'),
    ('R-209', 'Papa Johns', '29 Church Street'),
    ('R-210', 'Subway', '7 Pope Avenue');

```

<img width="203" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/8282eabc-d696-4587-ac80-2d7dccb99ea4">
