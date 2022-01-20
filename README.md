# Node DB3 Guided Project

Guided project for **Node DB3** Module.

## Prerequisites

- [SQLite Studio](https://sqlitestudio.pl/index.rvt?act=download) installed.
- [This Query Tool Loaded in the browser](https://www.w3schools.com/Sql/tryit.asp?filename=trysql_select_top).
- a rest client like [Insomnia](https://insomnia.rest/download/) or [Postman](https://www.getpostman.com/downloads/) installed.

## Project Setup

- [ ] clone this repository.
- [ ] cd into the project folder.
- [ ] type `npm i` to download dependencies.
- [ ] type `npm run server` to start the API.

Please follow along as the instructor creates database access methods for a multi table schema.


```
npm show knex versions 
npm uninstall knex @vscode/sqlite3
npm install knex@0.95.15 sqlite3


northwind:
select * from orders;
select * from Shippers;
select * from customers;
select * from products;

select * from orders join shippers;
select * from orders join shippers on orders.ShipperID = shippers.ShipperID;
select * from orders 
 join shippers on orders.ShipperID = shippers.ShipperID
 join customers on customers.CustomerID = orders.CustomerID;

 select orderid, customername, shippername from orders 
  join shippers on orders.ShipperID = shippers.ShipperID
  join customers on customers.CustomerID = orders.CustomerID;

select orderid, customername, shippername from orders as o
 join customers as c
    on c.CustomerID = o.CustomerID
 join shippers as s
    on o.ShipperID = s.ShipperID; 

select o.orderid, c.customername, s.shippername from orders as o
 join customers as c
    on c.CustomerID = o.CustomerID
 join shippers as s
    on o.ShipperID = s.ShipperID;
select productid, productname, categoryname
  from products as p 
  join categories as c
    on p.categoryid = c.categoryid;

select productid, productname, categoryname
  from products as p 
  join categories as c
    on p.categoryid = c.categoryid
  group by c.categoryid;

select  categoryname, count(p.productid)
  from products as p 
  join categories as c
    on p.categoryid = c.categoryid
  group by c.categoryid;

select  categoryname, count(p.productid) as prod_count
  from products as p 
  join categories as c
    on p.categoryid = c.categoryid
  group by c.categoryid;

select  categoryname, count(p.productid) as prod_count
  from products as p 
  join categories as c
    on p.categoryid = c.categoryid
  group by c.categoryid
  order by prod_count desc;

select orderid, firstname 
  from orders as o
  join employees as e
    on o.employeeid = e.employeeid;
select orderid, firstname 
  from orders as o
  left join employees as e
    on o.employeeid = e.employeeid;

select orderid, firstname 
  from employees as e
  left join orders as o
    on o.employeeid = e.employeeid;

select (firstname  || ' ' || lastname) as employee, count()
  from employees as e
  left join orders as o
    on o.employeeid = e.employeeid
    group by e.employeeid;

select (firstname  || ' ' || lastname) as employee, count() as order_count
  from employees as e
  left join orders as o
    on o.employeeid = e.employeeid
    group by e.employeeid
    order by order_count desc;

select * from users as u
 join posts as p
    on p.user_id = u.id;

select * from users as u
 left join posts as p
    on p.user_id = u.id;

select * from posts as u
 left join users as p
    on p.user_id = u.id;

select * from posts as p
 left join users as u
    on u.id = p.user_id ;

select * from posts as p
 left join users as u
    on u.id = p.user_id where u.id=3;

select contents, username, id 
 from posts as p
 left join users as u
    on u.id = p.user_id where u.id=2;
select contents, username, id as post_id
 from posts as p
 left join users as u
    on u.id = p.user_id where u.id=2;


https://stackoverflow.com/questions/5706437/whats-the-difference-between-inner-join-left-join-right-join-and-full-join

```