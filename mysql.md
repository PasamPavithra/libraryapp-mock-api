# bankapp-mock-api MYSQL

#### Task 1: Create Database
```
create database pavithra_db;
use database_db;
```

#### Task 1: Register Table
```
create table register (
id int primary key auto_increment,
name varchar(40) NOT NULL,
email varchar(50) NOT NULL,
password varchar(30) NOT NULL,
role varchar(10) NOT NULL default 'USER',
active boolean NOT NULL default 1,
unique(email),
check (role in ('USER','ADMIN'))
);
```

#### Task 1.1: Insert values into Register table
```
insert into register (name,email,password,role) values ( 'Pavi','pavi@gmail.com', '123', 'ADMIN');
insert into register (name,email,password,role) values ( 'Pasam','pasam@gmail.com', '456', 'USER');
insert into register (name,email,password,role) values ( 'sushmita','sushmita@gmail.com', '789', 'USER');
```

#### Task 1.2: List all Register
```
select * from register;


```

#### Task 2: Login table
```
create table login(
id int primary key auto_increment,
login_id int NOT NULL,
email varchar(20) NOT NULL,
password varchar(10) NOT NULL,
role varchar(10) NOT NULL,
check (role in ('USER','ADMIN')),
foreign key (login_id) references register(id)
);
```

#### Task 2.1: Insert values into Login table
```
insert into login(email,password,role) values ('pasam@gmail.com','222','ADMIN');
insert into login(email,password,role) values('pavi@123gmail.com','111','USER');
```

#### Task 2.2: List login 
```
selelct * from login where role='ADMIN';
selelct * from login where role='USER';
```

#### Task 3: Creating books table
```
create table book (
bookid int primary key auto_increment,
title varchar(40) NOT NULL,
author varchar(50) NOT NULL,
publisher varchar(30) NOT NULL,
category varchar(10) NOT NULL
);
```

#### task 3.1: Inserting values into book 
```
insert into book (title,author,publisher,category) values ( 'Advance SE','Athreya', 'naveeneeti', 'CSE');
insert into book (title,author,publisher,category) values ( 'Multiprocessor','Narayan', 'naveneeti', 'ECE');
insert into book (title,author,publisher,category) values ( 'DigitalSignals','Athreya', 'Master', 'ECE');
```

#### Task 3.2: List book 
```
select * from book where author='athreya';
select * from book where publisher='naveneeti';
select * from book where category='CSE';
```
#### Task 4: Creating borrow books table
```
create table borrow (
bookid int primary key auto_increment,
id int NOT NULL,
title varchar(40) NOT NULL,
author varchar(50) NOT NULL,
publisher varchar(30) NOT NULL,
category varchar(10) NOT NULL,
created_date timestamp not null default current_timestamp,
return_date timestamp not null default current_timestamp on update current_timestamp,
unique(id),
foreign key(id) references book(bookid)
);
```
#### task 4.1: Inserting values into borrow table 
```
insert into borrow (title,author,publisher,category) values ( 'Advance SE','Athreya', 'naveeneeti', 'CSE');
insert into borrow (title,author,publisher,category) values ( 'Multiprocessor','Narayan', 'naveneeti', 'ECE');
insert into borrow (title,author,publisher,category) values ( 'DigitalSignals','Athreya', 'Master', 'ECE');
```
#### Task 4.2: List brrow table
```
select * from borrow;

```
