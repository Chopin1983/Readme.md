# 'Get a job'
This project was created to find a job.
It consists of four parts.

## Terminy produktu
## Fortuna-1-liga
## Mapa Polski
## Obliczanie pól

## - Terminy produktu (expiry date) 
It was created, because the company which I work in, give us reimbursement for things to wear,
but every thing has different "expiry date", and the reimbursement amount.
What does it mean? 
You can buy a t-shirt, but only one during the year, you can spend 100zł for it.
You can buy more expensive clothes, but if you have for more money you pay the difference.
You can also buy shoes, but this time only one pair each two years. You have 250zł for that purchase.
For more details, I invite you to check this project.
Because nobody cares about it, I think to myself 'Maybe I'll do something interesting what can help"
And this is how this project started.

## - Fortuna-1-liga (Fortuna first league)
This project was created, because I'm football fan, and my beloved club plays in the second division. (I don't know how it happened).
You can see, how "Fortuna 1 liga" (This is the name of our second division) presented after 33 rounds, details of every match.
You can insert details from current season and update table alive.

## - Mapa Polski (Polish map)
For about fifteen years I worked as a sales representative, so I used to drive a car a lot by using Google Maps.
I have always wondered, how it's like to make a map.
That was my first thing, when I started to study SQL, so I made a very small part of it.

## - Obliczanie pól (field counting)
This is very simple project.
You can calculate fields for a few shapes like triangle, rectangle, square or circle.
Why did I do it? I don't know... This is one of the first thing which I made during learning SQL.

#  Technology used
- SQL/T-SQL
- MSSQL

#  Install

##  Terminy produktu
- Create Table -> "Positions", "Products", "Employee", "Transaction" in this order.
- Insert Values into these tables using INSERT INTO for "Position", and BULK INSERT for "Products" and "Employee".
  If You want to Insert Your values, You have to Insert them by:

  Examples:

   ```sql
             INSERT INTO Products (ID_Product,Position,Product_Name,Expiry_Date,Refund_Amount)
             Values ('1A',1,'Ubranie robocze (bluza, spodnie)',48,170)

             INSERT INTO Employee (ID_Employee,Name,Last_Name,Street,Nr_Building,Nr_Apartment,City,Zip,PESEL,Phone,Sex,ID_Position)
             Values (1,'Sebastian','Es','Drogowa',12,7,Kraków,30000,12345678900,790000000,'M',1)


- Create View "Term_Table". Now You can see every not expired product
- Create procedure "Inserting_Transaction", now You can start inserting bills.
  This procedure except inserting has blocking function, which doesn't allow You to insert new invoices or recipts,
  if last bought product from the same kind hasn't expired. If it has, You will see this warning.
         `Invoice can't be inserted, because the expiration date hasn't expired`
   
- Create View "Term_Table". Now You can see every not expired product.

  #### Those Tables are protected by triggers, which observing illegal activity like deleting or updating.
  #### If You are not interest this solution skip next move, if You are, continue instalation process.
- Create Table "Transactions_Deleted" and Trigger "Trigger_Delete"
- Create Table "Transactions_Update" and Trigger "Trigger_Update"
- Create Table "Table_Available_Orders" and insert into values

  #### Every available commands can be checked by:
  ```sql
           Select * from Table_Available_Orders

##  Fortuna-1-liga
  - Create table -> Matches, all tables with team lineups, Players, Match_Details in this order
  - Bulk insert all ready tables, or insert Yours by:
    Note: Every club has own code, like bottom. Wisła Kraków has numbers between 100 and 199.
    It consist of 1 - is number of the team, 30 - is ID of the player (not on a T-shirt) in this team.

  Example:
  
  ```sql
      INSERT INTO Players (ID_Player,ID_Team,Players_Name,Nr,Position,Date_Of_Birth)
      Values (130,'WisKra','Ángel Rodado',9,'Środkowy napastnik','1997-03-07')


