
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

#### Table Population

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

### 3.3.  Create 'Items' Table 
<img width="207" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/df464c68-2877-41d3-b3bc-2d1ceff9cc8a">

#### Data Types and Constraints
* The Primary Key is Item_ID because it uniquely identifies each item in an order.
* DECIMAL (8,2) specifies that the price column will have a maximum of 8 digits and set to 2 decimal points.
* Item name and category are VARCHAR because their character length can vary.
* The CHECK CONSTRAINT prevents zero or negative values by enforcing that Price contains values greater than 0.
* NOT NULL constraint was used to ensure that certain columns like Item_ID, price and item_name are not left empty.

#### Table Population

``` mysql

-- Populate Items Table
INSERT INTO Items VALUES
    (101, 'Burger', 8.9, 'Main Course'),
    (102, 'Pizza', 12.99, 'Main Course'), 
    (103, 'Water', 1.80, 'Drinks'),
    (104, 'Fries', 12, 'Starter'),
    (105, 'Chicken Wings', 7.3, 'Main Course'),
    (106, 'Coke', 1.99, 'Drinks'),
    (107, 'Steak', 8.90, 'Main Course'),
    (108, 'Garlic Bread', 5.99, 'Starter'),
    (109, 'Jollof Rice', 9.90, 'Main Course'),
    (110, 'Asun', 5.8, 'Starter');

```

<img width="161" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/a8d66e05-cbf9-4b2e-9489-5c9d2b225dc4">

### 3.4.  Create 'Manager' Table 

<img width="175" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/68e40e14-c836-433f-9db7-86a76b3fe7f4">

#### Data Types and Constraints
* The Primary Key is Manager_ID because it uniquely identifies each manager.
* VARCHAR was used for ID and manager’s name because character length can vary.
* NOT NULL specifies that each manager must be associated with a Manager_ID and Manager_Name.

#### Table Population

``` mysql

-- Populate Manager Table
INSERT INTO Manager VALUES
    ('M-01', 'Arthur Nweke'),
    ('M-02', 'Chidinma Oloni'),
    ('M-03', 'Nitsa Ning'),
    ('M-04', 'Kevin Hong'),
    ('M-05', 'Faizah Sani'),
    ('M-06', 'Jude Chris'),
    ('M-07', 'Mike Ohis'),
    ('M-08', 'Chrystal Green'),
    ('M-09', 'Pamela Okenwa'),
    ('M-10', 'Ogonna Uzo');

```
<img width="150" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/1ba2673e-645c-43c8-b4be-72f342f3b4c3">

### 3.5.  Create Driving License table 

<img width="149" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/177b38fd-aff2-492c-b37e-ffa9894c8fa9">

#### Data Types and Constraints
* The Primary Key is License_ID because it uniquely identifies each driver’s license.
* VARCHAR was used because character lengths can vary.
* NOT NULL specifies that each driver’s license must be associated with an ID and expiry date. 

#### Table Population

``` mysql

-- Populate Driving_License Table
INSERT INTO Driving_License VALUES
    ('DL-12345', '2020-05-10', 'UK', '2025-05-10'),
    ('DL-67890', '2019-08-20', 'UK', '2024-08-20'),
    ('DL-12875', '2020-05-18', 'UK', '2025-05-18'),
    ('DL-97854', '2019-09-28', 'UK', '2024-09-28'),
    ('DL-56394', '2020-01-10', 'USA', '2025-01-10'),
    ('DL-23876', '2019-01-20', 'UK', '2024-01-20'),
    ('DL-12376', '2020-05-01', 'USA', '2025-05-01'),
    ('DL-67871', '2019-08-05', 'UK', '2024-08-05'),
    ('DL-89764', '2020-03-10', 'Canada', '2025-03-10'),
    ('DL-32123', '2019-02-20', 'UK', '2024-02-20')
    ;

```

<img width="202" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/b57f8328-2a38-448e-9d90-800fbd409c15">


### 3.6.  Create Vehicle Table 

<img width="151" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/b54ae7a8-e08f-4f71-9e68-a711981debdb">

#### Data Types and Constraints
* The Primary Key is Vehicle_ID because it uniquely identifies each vehicle/motorcycle.
* VARCHAR was used to store values of variable character length.
* NOT NULL specifies that each vehicle must be associated with a vehicle_id and registration_number.
* Decimals are allowed for engine size, but they will be rounded to 2 decimal points.

#### Table population

``` mysql

-- Populate Vehicle Table
INSERT INTO Vehicle VALUES

    (1, 'AB-193', 'Red', '2022-01-15', 1.687),
    (2, 'CD-456', 'Blue', '2019-11-20', 2.0),
    (3, 'FF-123', 'Black', '2023-06-15', 1.678),
    (4, 'PO-470', 'White', '2021-05-20', 2.09),
    (5, 'HS-763', 'Red', '2022-01-15', 2.67),
    (6, 'TM-336', 'Grey', '2021-11-25', 2.08),
    (7, 'WS-111', 'Black', '2022-01-18', 1.0),
    (8, 'LK-326', 'White', '2022-11-20', 2.70),
    (9, 'WS-111', 'Black', '2022-01-09', 1.9),
    (10, 'LK-326', 'White', '2022-11-04', 2.18);

```

<img width="214" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/e2ffbdfa-0ee4-4eba-817e-c4e799c2fca2">

### 3.7.  Drivers Table Creation

<img width="205" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/a9992d85-425b-4cb5-8cfe-aa443ccc1fba">

#### Data Types and Constraints
* The Primary key is Driver_ID because it uniquely identifies each driver employed by Kanagaroo.
* The Foreign Keys are Manager_ID, Restaurant_ID, Vehicle_ID and License_ID. They establish a relationship between their table and the Driver table. For example, 
 Manager_ID establishes a relationship between drivers and managers whereby each driver is assigned to a manager.
* NOT NULL specifies that every driver must be associated with a Driver_ID, Driver_Name, Restaurant_ID, Manager_ID, Vehicle_ID and License_ID.
* VARCHAR was used to store values of variable length.

#### Table Population
``` mysql

-- Populate Drivers Table
INSERT INTO Drivers VALUES
    ('DR-01', 'Jennifer Anniston', 'jenny.a@gmail.com', 3000.00, 'R-201', 'M-01', 1, 'DL-12345'),
    ('DR-02', 'Barrack Obama', 'barryo@yahoo.com', 2800, 'R-202', 'M-02', 2, 'DL-12376'),
    ('DR-03', 'Shonda Rhimes', 'shonda.r@yahoo.com', 3100.1, 'R-203', 'M-03', 3, 'DL-12875'),
    ('DR-04', 'Bill Gates', 'billyg@yahoo.com', 2800.40, 'R-204', 'M-04', 4, 'DL-23876'),
    ('DR-05', 'Elon Musk', 'elonmusk@yahoo.com', 2800, 'R-201', 'M-05', 5, 'DL-32123'),
    ('DR-06', 'Steve Jobbs', 'steviej@rocketmail.com', 2890.90, 'R-206', 'M-06', 6, 'DL-56394'),
    ('DR-07', 'Oprah Winfrey', 'oprah.w@yahoo.com', 2400.0, 'R-207', 'M-07', 7, 'DL-67871'),
    ('DR-08', 'Margaret Thatcher', 'maggie.t@gmail.com', 2230.00, 'R-208', 'M-03', 8, 'DL-67890'),
    ('DR-09', 'Bill Clinton', 'bill.clinton@gmail.com', 2230.00, 'R-202', 'M-02', 9, 'DL-89764'),
    ('DR-10', 'Michael Jackson', 'michael.j@yahoo.com', 2800.00, 'R-210', 'M-01', 10, 'DL-97854');

```

<img width="399" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/6b4e4cc7-e1cb-4a80-9561-32902e0b0077">

### 3.8.   Orders Table Creation

<img width="327" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/72588ead-8db9-45f8-a599-7cda3cbd7c09">

#### Data Types and Constraints
* The Primary Key is Order_ID because it uniquely identifies each order. Its’ data type is CHAR (10), and it stores a maximum length of 10 characters.
* NOT NULL specifies that every order must be associated with a customer_ID, Restaurant_ID, Item_ID, Driver_ID.
* The default CURRENT_TIMESTAMP specifies that the current date and time must be assigned to the Order Date column when a new order is placed or entered.
* Order_Amount can allow decimals with a maximum of 8 digits and 2 decimal places.
* A foreign key constraint on Customer_ID establishes a relationship between customer and orders table, whereby each order_ID must be assigned to a customer_ID.
* ON DELETE CASCADE specifies that if a customer is deleted, all orders associated with that customer will be deleted.


#### Table Population

``` mysql

-- Populate Orders Table
INSERT INTO Orders VALUES
    ('OR-101', '2023-02-01', 20, 'C-01', 101, 'R-201','DR-01'),
    ('OR-102', '2023-02-02', 30.5, 'C-02', 102, 'R-202', 'DR-02'),
    ('OR-103', '2023-02-06', 25.1, 'C-01', 101, 'R-203', 'DR-03'),
    ('OR-104', '2023-02-06', 17.0, 'C-03', 103, 'R-203', 'DR-03'),
    ('OR-105', '2023-02-10', 20, 'C-04', 104, 'R-204', 'DR-04'),
    ('OR-106', '2023-02-11', 15.50, 'C-05', 105, 'R-205', 'DR-05'),
    ('OR-107', '2023-02-12', 50, 'C-06', 106, 'R-206', 'DR-06'),
    ('OR-108', '2023-02-13', 40.60, 'C-01', 107, 'R-207', 'DR-07'),
    ('OR-109', '2023-02-13', 15.99, 'C-07', 108, 'R-207', 'DR-07'),
    ('OR-110', '2023-02-13', 12.5, 'C-08', 109, 'R-208', 'DR-08');

```

<img width="318" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/0ecf5bf9-dc39-4b67-bc26-75394f29da20">


### 3.9.   Payroll Table Creation

<img width="224" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/90cd5d6b-0ce1-46bd-a62b-d3cccb658a0a">

#### Data Types and Constraints
* The Primary Key is Payroll_ID because it uniquely identifies each payroll.
* NOT NULL specifies that each payroll_ID is associated with a driver ID and National insurance number.
* The foreign key is Driver_ID. It establishes a relationship between driver table and payroll table. Each payroll_ID must be assigned to a driver_ID.

#### Table Population

``` mysql

-- Populate Payroll Table
INSERT INTO Payroll VALUES
    ('P-101', 'DR-01', 'NI123456'),
    ('P-102', 'DR-02', 'NI789012'),
    ('P-103', 'DR-03', 'NI123456'),
    ('P-104', 'DR-04', 'NI309012'),
    ('P-105', 'DR-05', 'NI709456'),
    ('P-106', 'DR-06', 'NI430012'),
    ('P-107', 'DR-07', 'NI009656'),
    ('P-108', 'DR-08', 'NI907612'),
    ('P-109', 'DR-09', 'NI887656'),
    ('P-110', 'DR-10', 'NI112912');

```

<img width="153" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/6cd565b3-d84e-4afc-9481-615625dc95d3">


## 4.   Application of Database Design to Business Processes

This Kangaroo database can be used to create, read, update and delete data for business needs.

### 4.1.   Business Case 1: Update Customer Table
* Update the email address of customer with ID ‘C-01’ from kelechi.u@yahoo.com to kelechi94@gmail.com.
* Add a new customer to the database.

``` mysql

-- Update Customer table
    UPDATE Customers
    SET Customers.Email = 'kelechi94@gmail.com'
    WHERE Customer_ID = 'C-01';
    
-- Add a new customer to customer table
    INSERT INTO Customers VALUES  
    ('C-11', 'Saber', 'Farag', 'saber.farag@ymail.co.uk', '07898453109');

```
<img width="290" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/130cd678-89f9-4383-9524-d97e87c9e69d">


The UPDATE statement is used to update records in the customer table. The SET statement changes the email address in the Email column. The WHERE clause specifies that only the row where the customer ID is ‘C-01’ will be updated. The INSERT INTO clause adds a new customer with ID ‘C-11’ to the customer table.

### 4.2.	   Business Case 2: Most Popular Restaurant
Find the restaurant with the most orders.

``` mysql

SELECT r.Restaurant_ID,
r.Restaurant_Name,
COUNT(o.Order_ID) AS Total_Orders
FROM Restaurants r
LEFT JOIN Orders o
ON r.Restaurant_ID = o.Restaurant_ID
GROUP BY r.Restaurant_ID, r.Restaurant_Name
ORDER BY Total_Orders DESC;

```

<img width="273" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/3dc4cbd8-f187-48bc-a06f-458f3839ca12">

The restaurants with the most orders are Wendys and Green Kitchen with two orders each. Papa Johns and Subway have zero orders.
The COUNT function counts the number of orders for each restaurant and labels it Total_Orders. The LEFT JOIN clause includes all restaurants in the restaurant table, even if they have no orders. The ON condition creates a relationship between both tables through the Restaurant_ID. The GROUP BY clause groups the result by restaurant ID and restaurant name. The ORDER BY clause orders the results by Total_Orders in descending order.


### 4.3.  Business Case 3: Busiest Day of the Week

Find the busiest day of the week. This can be done by extracting the day from date.

``` mysql

SELECT TOP 1
DATENAME (weekday, Order_Date) AS Busiest_Day,
COUNT(*) AS Total_Orders
FROM Orders
GROUP BY DATENAME (weekday, Order_Date)
ORDER BY Total_Orders DESC;

```

<img width="232" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/1342dba4-eb32-4e0d-ac7e-e2761b0ae8af">

The busiest day of the week is Monday. The COUNT function counts the total orders received each day and labels it as Total_Orders. The DATENAME function extracts the name of the week from order_date. The TOP 1 constraint only returns the first row. The results are GROUPED BY the weekday.

### 4.4.  Business Case 4: Most Frequent Customer

``` mysql

SELECT 
c.Customer_ID,
c.First_Name,
COUNT(o.Order_ID) AS Total_Orders
FROM Customers c
LEFT JOIN Orders o
ON c.Customer_ID = o.Customer_ID
GROUP BY c.Customer_ID, c.First_Name
ORDER BY Total_Orders DESC;

```

<img width="208" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/3d2f8dce-e3c2-451e-a566-7473e21d13aa">

The most frequent customer is Kelechi with a total of 3 orders. Ken, Chinwe and Saber have zero orders. 

### 4.5.  Business Case 5: Busiest Driver

``` mysql

SELECT 
    d.Driver_ID, 
    d.Driver_Name,
    COUNT(o.Order_ID) AS Total_Orders
FROM 
    Drivers d 
    LEFT JOIN Orders o
ON 
    d.Driver_ID = o.Driver_ID
GROUP BY d.Driver_ID, d.Driver_Name
ORDER BY Total_Orders DESC;

```
<img width="182" alt="image" src="https://github.com/kelechiu/Relational_Database_Design_SQL/assets/100145388/10b11a60-fddb-4013-83f5-acef9ddd6e1f">

The busiest drivers are Shonda Rhimes and Oprah Winfrey with 2 orders each. The LEFT JOIN clause ensures all drivers are included in the results, even those without orders. It joins both driver and orders table through their driver_ID. The COUNT function counts the total number of order_id for all drivers and labels it as Total_Orders. The ORDER BY clause orders the result by Total-orders in descending order.
