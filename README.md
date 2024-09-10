# 'Get a job'
This project was created to find a job.
It consists of four parts

## Terminy produktu
## Fortuna-1-liga
## Mapa Polski
## Obliczanie pól

## - Terminy produktu (expiry date) 
Was created, because in company where I work, we're geting things to wear for free,
but everyone has different "expiry date".
What its mean? 
You can buy some t-shirt, but only one in one year period.
You can buy shoes, but this time only couple in two years period.
For more details, I invite you to check this project.
Because nobody care about this, i think to my self 'Maybe i do something interesting, that what can help"
And this is how this project had started.

## - Fortuna-1-liga (second division in Polish football league)
This project was created, because I'm football fan, and my love club play in second division "I don't know how it happend".
You can see, how "Fortuna 1 liga" (This is name of our second division) looked after 33 rounds, detail every match.
You can insert details from current season and update table alive.

## - Mapa Polski (Polish map)
About fifteen years I worked as sales representative, so I had been driving a car a lot by using Google Maps.
I'm allways wondering, how it's like to make a map.
That was my first thing, when i started study SQL, so I made a very small part of it.

## - Obliczanie pól (field counting)
This is very simple project.
You can count field for few shapes like triangle,  rectangle, square or circle.
Why i did it? I don't know... This is one of the first thing which I made during lerning SQL.

#  Technology used
- SQL/T-SQL
- MSSQL

#  Install

##  Terminy produktu
- Create table -> Positions, Products, Employee, Transaction in this order.
- Insert values into these tables using INSERT INTO for Position, and BULK INSERT for the rest.
  If You want to Insert Your values, You have to Insert them by:

  Examples:

   '''sql
            "INSERT INTO Products (ID_Product,Position,Product_Name,Expiry_Date,Refund_Amount)
             Values ('1A',1,'Ubranie robocze (bluza, spodnie)',48,170)

            "INSERT INTO Employee (ID_Employee,Name,Last_Name,Street,Nr_Building,Nr_Apartment,City,Zip,PESEL,Phone,Sex,ID_Position)
             Values (1,'Sebastian','Es','Drogowa',12,7,Kraków,30000,12345678900,790000000,'M',1)

            "INSERT INTO Transactions (Nr,Foreign_Number,Company,TIN,Product_Name,Product_Value,Date_Od_Purchase,ID_Product,ID_Employee)
             Values (1,'FA/2022/11','Guliwer',2345678901,'Bluza',230.00,'2022-11-12','1A',2)



- Create View Term_Table. Now You can see every not expire products
- 
