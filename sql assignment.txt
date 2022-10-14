Create Database Sample1
Create Table Customerss
(
CosID int primary key,
FirstName nvarchar(40),
LastName nvarchar(40),
City nvarchar(40),
Country nvarchar(40),
Phone nvarchar(30)
);
select * from Customerss;
create index Customerssname on Customerss( LastName,FirstName);
insert into Customerss values(2011,'samruddhi','trimbake','nagpur','india',1234567898);
insert into Customerss values(2012,'ruthuja','yalawar','nanded','india',1236787898);
insert into Customerss values(2013,'riddhi','shirole','pune','india',3454567898);
insert into Customerss values(2014,'suju','sarkar','suhk','Germany',1234567798);
insert into Customerss values(2015,'saurabh','jadhav','ert','canada',0300074321);
insert into Customerss values(2016,'jon','dukh','murmur','America',1234567898);
insert into Customerss values(2017,'pinki','barde','nasikh','india',1290867898);
select * from Customerss;

Create Table Orderss
(
id int primary key,
OrderDate datetime,
OrderNumber nvarchar(10),
CustomerssID int,
TotalAmount decimal(12,2)
);
select * from Orderss;
alter table Orderss
add constraint fk_Orderss foreign key(CustomerssID)references Customerss (CustomerssID);
select * from Customerss;
select * from Orderss;
EXEC sp_rename 'Orderss.Ordid', 'Ord_id','column';
EXEC sp_rename 'Customerss.CosID', 'Cos_ID', 'column';
EXEC sp_rename 'Orderss.CosID', 'Cos_ID', 'column';
create index idx_Cos_ID on Orderss (Cos_ID);
create index idx_OrderDate on Orderss (OrderDate);
insert into Orderss values(3100,26-02-2000,102,1012,2010);
insert into Orderss values(3101,16-04-2000,103,1012,2510);
insert into Orderss values(3102,05-06-2000,104,1012,2610);
insert into Orderss values(3103,09-05-2000,105,1012,2910);
insert into Orderss values(3104,12-03-2000,106,1012,2310);
insert into Orderss values(3105,11-12-2000,107,1012,2210);
insert into Orderss values(3106,23-11-2000,108,1012,2710);

Create Table Orderss
(
id int primary key,
OrderDate datetime,
OrderNumber nvarchar(10),
CustomerssID int,
TotalAmount decimal(12,2)
);
insert into Orderss values(3100,26-02-2000,102,1012,2010);
insert into Orderss values(3101,16-04-2000,103,1012,2510);
insert into Orderss values(3102,05-06-2000,104,1012,2610);
insert into Orderss values(3103,09-05-2000,105,1012,2910);
insert into Orderss values(3104,12-03-2000,106,1012,2310);
insert into Orderss values(3105,11-12-2000,107,1012,2210);
insert into Orderss values(3106,23-11-2000,108,1012,2710);
select * from Orderss;

create table OrderItem
(
id int primary key,
Orderid int,
Productid int,
UnitPrice decimal(12,2),
Quantity int
);
select * from OrderItem;
insert into OrderItem values(2,2,2,116.00,4);
insert into OrderItem values(3,3,3,678.00,4);
insert into OrderItem values(4,4,4,456.00,4);
insert into OrderItem values(5,5,5,234.00,4);
insert into OrderItem values(6,6,6,567.00,4);
insert into OrderItem values(7,7,7,987.00,4);
insert into OrderItem values(8,8,8,598.00,4);

select * from OrderItem;
create index idx_OrderItem on OrderItem(Orderid);
create index idx_Order_pro_item on OrderItem(pro_id);
create table product
(
pro_id int primary key,
productname nvarchar(50),
unitprice decimal(12,2),
package nvarchar(30),
isdiscontinued bit
);
select * from product;
insert into product values(11,'x',234.00,4,1);
insert into product values(12,'y',456.00,3,2);
insert into product values(13,'z',789.00,5,3);
insert into product values(14,'a',987.00,6,5);
insert into product values(15,'b',543.00,8,7);
insert into product values(16,'c',321.00,7,8);
insert into product values(17,'k',378.00,9,6);
select * from product;


SELECT Country from Customerss
where Country like 'A%'


SELECT Country from Customerss
where Country like 'i%'

SELECT * from Customerss 
WHERE LastName like '__i%';

select * from  Customerss;

SELECT * from Customerss
where Country like 'Germany';

SELECT FirstName,LastName 'FullName' from Customerss;

SELECT * from Customerss
WHERE LastName like '_u%';

SELECT * from Customerss
WHERE FirstName like '_u%';

SELECT UnitPrice from OrderItem 
WHERE UnitPrice>'10' and UnitPrice<'20';

SELECT OrderDate 'shipping' from Orderss
ORDER BY  OrderDate DESC;

insert into product values(111,'exotic liquids',123.0,'yes',0);
select * from product;

select productname from product
where productname like 'exotic liquids';

select AVG(unitprice) from product;
alter table Customerss add fax_number int;
select * from Customerss;

alter table Orderss add shipping_name nvarchar(40),shipping_date date;
select * from Orderss;

alter table product add category nvarchar(40);
select * from product;

create table employee
(
emp_id int,
emp_name nvarchar(40),
depart_name nvarchar(40),
manager_name nvarchar(40),
joining date,
rating int
);
select * from employee;
insert into employee values(11,'samruddhi','incometax','payal','2002-05-13',4);
insert into employee values(12,'prashant','fax','raj','2002-08-19',3);
insert into employee values(13,'amit','desk','yog','2002-08-17',2);
insert into employee values(14,'vijay','head','meet','2002-10-14',5);
insert into employee values(15,'shweta','service','shratik','2002-12-11',4);
insert into employee values(16,'riddhi','hr','soham','2002-02-12',3);
insert into employee values(17,'siddhi','payroll','guru','2002-09-15',5);
select * from employee;

insert into product(category) values('seafood');
select fax_number from Customerss;

select emp_name , manager_name from employee;

select distinct productname,unitprice,category_name
from product
where unitprice>(select AVG(unitprice) from product)
order by unitprice;

alter table product add category_name nvarchar(40);
select * from product;

alter table product add price_after_discount nvarchar(40);
select * from product;

select distinct productname,unitprice,category_name,price_after_discount
from product
where unitprice>(select AVG(unitprice) from product)
order by unitprice;

select pro_id, isnull (category,'seafood') category from product;

select * from Orderss,product where TotalAmount >'50'and  productname like 'exotic liquids';

select ordernumber,phone from Orderss,Customerss;

select category from product where category like 'seafood';

select ordernumber,country from Orderss,Customerss where country like 'india';

select ordernumber ,productname from Orderss,product where productname like 'chai';

select emp_name,depart_name,rating from employee where emp_name like 'samruddhi';

select * from Orderss,product where TotalAmount >'50'and  productname like 'exotic liquids';

select min(joining) as earlistdate from employee;

select max(joining) as earlistdate from employee;

alter table product add out_of_stock nvarchar(40), unitinstock decimal(12,2),unitoutstock decimal(12,2);
select out_of_stock,unitinstock,unitoutstock from product;


SELECT productname, unitprice 
FROM product
ORDER BY unitprice DESC;

alter table product add unitinstock nvarchar(40);
select * from product;

alter table product add  unitonorder nvarchar(40);
select * from product;

SELECT productname, unitinstock, unitonorder 
FROM product
WHERE (unitinstock<unitonorder);



select pro_id,productname,unitprice,category
from product
where (unitprice<20)
order By unitprice DESC;

SELECT Orderss.OrderNumber, Customerss.CosID
FROM Orderss, Customerss
WHERE Orderss.CosID= Customerss.CosID;


SELECT CustomerssID from Orderss
where CustomerssID like '1012';

alter table product add companyname nvarchar(40);
select * from product;

SELECT * from product
WHERE companyname like 'NULL';
