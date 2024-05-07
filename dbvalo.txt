Internet and Cable Tv bill payment project:
Tables:
1. Service Providers
2. Services
3. Users
4. Bills
5. Transactions


Service Providers:
   - ProviderID (Primary Key)
   - ProviderName
   - ProviderType
   
Services:
   - ServiceID (Primary Key)
   - ProviderID (Foreign Key)
   - ServiceName
   - Description
   
Users:
   - UserID (Primary Key)
   - Username
   - Password
   - Email
   - Phone
   - Address

Bills:
   - BillID (Primary Key)
   - UserID (Foreign Key)
   - ServiceID (Foreign Key)
   - Amount
   - DueDate
   - Status (Paid/Pending)
    

Transactions:
   - TransactionID (Primary Key)
   - UserID (Foreign Key)
   - BillID (Foreign Key)
   - Amount
   - Timestamp
   






--all table and insertion
create table serviceProviders (
    providerId int primary key,
    providerName varchar(100),
    providerType varchar(100)
);

create table services (
    serviceId int primary key,
    providerId int,
    serviceName varchar(100),
    description varchar(500),
    foreign key (providerid) references serviceproviders(providerid)
);

create table users (
    userId int primary key,
    username varchar(100),
    password varchar(100),
    email varchar(100),
    phone varchar(20),
    address varchar(500)
);

create table bills (
    billId int primary key,
    userId int,
    serviceId int,
    amount decimal(10,2),
    duedate date,
    status varchar(10),
    foreign key (userId) references users(userId),
    foreign key (serviceId) references services(serviceId)
);



create table transactions (
    transactionId int primary key,
    userId int,
    billId int,
    amount decimal(10, 2),
    timestamp timestamp default current_timestamp,
    foreign key (userId) references users(userId),
    foreign key (billId) references bills(billId)
);







--serviceProviders table
insert into serviceProviders (providerId, providerName, providerType) values(1, 'Internet Service Provider', 'Internet');
insert into serviceProviders (providerId, providerName, providerType) values(2, 'Streaming Service Provider', 'Entertainment');


--services table
insert into services (serviceId, providerId, serviceName, description) values(1, 1, 'Internet Basic', 'Basic internet plan with moderate speed');
insert into services (serviceId, providerId, serviceName, description) values(2, 1, 'Internet Premium', 'High-speed internet plan with premium features');
insert into services (serviceId, providerId, serviceName, description) values(3, 2, 'Streaming Basic', 'Basic streaming service with limited content');
insert into services (serviceId, providerId, serviceName, description) values(4, 2, 'Streaming Premium', 'Premium streaming service with access to exclusive content');


--users table
insert into users (userId, username, password, email, phone, address) values(1, 'babla2007045', 'password123', 'babla@gmail.com', '01751373323', 'LSH-KUET');
insert into users (userId, username, password, email, phone, address) values(2, 'abir2007049', 'amiabir49', 'abir@gmail.com', '01645678909', 'LSH-KUET');
insert into users (userId, username, password, email, phone, address) values(3, 'shafin2007043', '1234ffd', 'dhruba@gmail.com', '01645445665', 'LSH-KUET');
insert into users (userId, username, password, email, phone, address) values(4, 'rokon2007060', 'hufgkg', 'rokon@gmail.com', '01543765678', 'LSH-KUET');
insert into users (userId, username, password, email, phone, address) values(5, 'asif2007059', '678956yt', 'asif@gmail.com', '01789065432', 'LSH-KUET');
insert into users (userId, username, password, email, phone, address) values(6, 'sajib2007042', '2345th', 'sajib@gmail.com', '01664598765', 'LSH-KUET');
insert into users (userId, username, password, email, phone, address) values(7, 'ariful2007023', 'hu5767', 'ariful@gmail.com', '01543456788', 'FHH-KUET');
insert into users (userId, username, password, email, phone, address) values(8, 'sakib2007007', '678th9', 'asif@gmail.com', '01754675432', 'FHH-KUET');
insert into users (userId, username, password, email, phone, address) values(9, 'raihan2007005', '25345', 'sajib@gmail.com', '01664598754', 'FHH-KUET');




--bills table
insert into bills (billId, userId, serviceId, amount, duedate, status) values(1, 1, 1, 100, TO_DATE('2024-05-31', 'YYYY-MM-DD'), 'pending');
insert into bills (billId, userId, serviceId, amount, duedate, status) values(2, 2, 3, 300, TO_DATE('2024-05-31', 'YYYY-MM-DD'), 'paid');
insert into bills (billId, userId, serviceId, amount, duedate, status) values(3, 3, 2, 200, TO_DATE('2024-05-31', 'YYYY-MM-DD'), 'pending');
insert into bills (billId, userId, serviceId, amount, duedate, status) values(4, 4, 3, 300, TO_DATE('2024-05-31', 'YYYY-MM-DD'), 'paid');
insert into bills (billId, userId, serviceId, amount, duedate, status) values(5, 5, 4, 400, TO_DATE('2024-05-31', 'YYYY-MM-DD'), 'pending');
insert into bills (billId, userId, serviceId, amount, duedate, status) values(6, 6, 2, 200, TO_DATE('2024-05-31', 'YYYY-MM-DD'), 'paid');



--transactions table
insert into transactions (transactionId, userId, billId, amount) values(1, 2, 2, 29.99);
insert into transactions (transactionId, userId, billId, amount) values(2, 4, 4, 14.99);
insert into transactions (transactionId, userId, billId, amount) values(3, 6, 6, 14.99);












--1
create user database identified by 1234;

--2
grant all privileges to database;

--3
revoke all privileges from database;

--4
show user

--5
describe users

--6
select table_name from user_tables;

--7
select * from serviceproviders;

--8. all table selection
select * from serviceproviders;
select * from services;
select * from users;
select * from bills;
select * from transactions;

--9. drop all tables
drop table transactions;
drop table bills;
drop table users;
drop table services;
drop table serviceProviders;

--10
alter table users add nickName varchar(20);

--11
alter table users modify nickName varchar(23);

--12
alter table users rename column nickName to nickname2;

--14
alter table users drop column nickName2;

--15
select * from users where userId>=3;

--16
select * from users where userId=3;




--17
select * from serviceproviders where providerId = (select providerId from services where serviceName = 'Internet Basic');

--18
update services SET serviceName = 'Digital Electronics' where serviceId = (select serviceId from services where serviceName = 'Internet Basic');

--19
delete from serviceProviders where providerId = 2;

--20
select providerName from serviceProviders where providerName LIKE 'In%' union select providerName from serviceProviders where providerName LIKE 'I%';

-- 21
select count(*) from serviceProviders;

--22
select count(DISTINCT providerName) as number_of_providers from serviceProviders;

--23
select avg(servicecount) from (select count(*) as servicecount from services group by providerId);

--24
select SUM(servicecount) from (select count(*) as servicecount from services group by providerId);


--25
select * from serviceProviders where providerId IN (select providerId from (select providerId from services));

--26
select * from users where userId IN (select userId from bills where status = 'pending');

--27 Get the service providers along with the total amount of bills for each provider

select sp.providerId, sp.providerName, SUM(b.amount) as total_amount
from serviceProviders sp
JOIN services s ON sp.providerId = s.providerId
JOIN bills b ON s.serviceId = b.serviceId
group by sp.providerId, sp.providerName;

--28 Get the users along with the total number of bills and the sum of amounts for each user

select u.userId, u.username, count(b.billId) as total_bills, SUM(b.amount) as total_amount
from users u
LEFT JOIN bills b ON u.userId = b.userId
group by u.userId, u.username;




--29 A trigger which will update ststus when a new transaction is occured

CREATE OR REPLACE TRIGGER myTrigger
AFTER INSERT ON transactions
REFERENCING OLD AS o NEW AS n
FOR EACH ROW
BEGIN
    UPDATE bills
    SET status = 'paid'
    WHERE billId = :n.billId;
END;
/


--insert into transactions (transactionId, userId, billId, amount) values(4, 5, 5, 14.99);
--select * from transactions;
--show errors;
--drop trigger myTrigger;
