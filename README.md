# 'Get a job'
This project was created to find a job.
It consists of four parts

## Terminy produktu
## Fortuna-1-liga
## Mapa Polski
## Obliczanie pól

## - Terminy produktu (expiry date) 
Was created, because in company where I work, we have reimbursement for things to wearing,
but everyone has different "expiry date", and reimbursement amount.
What its mean? 
You can buy some t-shirt, but only one in one year period, and You can spend for it 100zł.
Of course You can buy more expensive clothes, but You have to pay for difference between reimbursement and product value.
You can also buy shoes, but this time only couple in two years period, and You have for that 250zł.
For more details, I invite you to check this project.
Because nobody care about it, i think to my self 'Maybe I'll do something interesting, that what can help"
And this is how this project started.

## - Fortuna-1-liga (Fortuna first league)
This project was created, because I'm football fan, and my love club play in second division "I don't know how it happened".
You can see, how "Fortuna 1 liga" (This is name of our second division) looked after 33 rounds, detail every match.
You can insert details from current season and update table alive.

## - Mapa Polski (Polish map)
About fifteen years I worked as sales representative, so I had been driving a car a lot by using Google Maps.
I had been allways wondering, how it's like to make a map.
That was my first thing, when I started study SQL, so I made a very small part of it.

## - Obliczanie pól (field counting)
This is very simple project.
You can calculate fields for few shapes like triangle,  rectangle, square or circle.
Why i did it? I don't know... This is one of the first thing which I made during lerning SQL.

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
            "INSERT INTO Products (ID_Product,Position,Product_Name,Expiry_Date,Refund_Amount)
             Values ('1A',1,'Ubranie robocze (bluza, spodnie)',48,170)

            "INSERT INTO Employee (ID_Employee,Name,Last_Name,Street,Nr_Building,Nr_Apartment,City,Zip,PESEL,Phone,Sex,ID_Position)
             Values (1,'Sebastian','Es','Drogowa',12,7,Kraków,30000,12345678900,790000000,'M',1)


- Create View "Term_Table". Now You can see every not expiry products
- Create procedure "Inserting_Transaction", now You can start inserting bills.
  This procedure except inserting has blocking function, which doesn't allow You to insert new invoices or recipt,
  if last bought product from same kind hasn't expired. If it's, You will see this warning.
         `Invoice can't be inserted, because the expiration date hasn't expired`
   
- Create View "Term_Table". Now You can see every not expire products.

  #### Those Tabels are protecting by triggers, which observing illegal activity like deleting or updating.
  #### If You are not interest this solution skip next move, if You are, continue instalation process.
- Create Table "Transactions_Deleted" and Trigger "Trigger_Delete"
- Create Table "Transactions_Update" and Trigger "Trigger_Update"
- Create Table "Table_Available_Orders" and insert into values

- Whole availeble commands can be cheked by:
  ```sql Select * from Table_Available_Orders
