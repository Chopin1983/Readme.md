# 'Get a job'
This project was created to find a job.
It consists of three parts.

### Terminy produktu
### Fortuna-1-liga
### Mapa Polski

## - Terminy produktu (expiry date) 
It was created, because the company where I work in gives us reimbursement for things to wear, but
every thing has a different "expiry date" and the reimbursement amount.
What does it mean? 
You can buy a T-shirt, but only one during the year, you can spend 100zł on it.
You can buy more expensive clothes, but if it costs more, you have to pay the difference.
You can also buy shoes, but this time only one pair every two years. You have 250zł for that purchase.
For more details, I invite you to check this project.
Because nobody cares about it, I think to myself 'Maybe I'll do something interesting that can help"
And this is how this project started.

## - Fortuna-1-liga (Fortuna first league)
This project was created, because I'm a football fan, and my beloved club plays in the second division. (I don't know how it happened).
You can see, how "Fortuna 1 liga" (This is the name of our second division) presented after 33 rounds, details of every match.
You can insert details from current season and update a table live.

## - Mapa Polski (Polish map)
For about fifteen years I worked as a sales representative, so I used to drive a car a lot by using Google Maps.
I have always wondered, what it's like to make a map.
That was my first thing, when I started studying SQL, so I made a very small part of it.

#  Technology used
- SQL/T-SQL
- MSSQL

#  Install

##  Terminy produktu
- Create Table -> "Positions", "Products", "Employee", "Transaction" in this order.
- Insert Values into these tables using INSERT INTO for "Position", and BULK INSERT for "Products" and "Employee".
  If You want to insert your values, you have to insert them by:

  Examples:

   ```sql
             INSERT INTO Products (ID_Product,Position,Product_Name,Expiry_Date,Refund_Amount)
             Values ('1A',1,'Ubranie robocze (bluza, spodnie)',48,170)

             INSERT INTO Employee (ID_Employee,Name,Last_Name,Street,Nr_Building,Nr_Apartment,City,Zip,PESEL,Phone,Sex,ID_Position)
             Values (1,'Sebastian','Es','Drogowa',12,7,Kraków,30000,12345678900,790000000,'M',1)
   ```

- Create View "Term_Table". Now You can see every available product "expiry product"
- Create procedure "Inserting_Transaction", now You can start inserting bills.
  This procedure has a blocking function, which doesn't allow you to insert new invoices or receipts,
  if the last product bought from the same categorie hasn't expired. If it has, You will see this warning.
         `Invoice can't be inserted, because the due date hasn't expired`
   
- Create View "Term_Table". Now You can see every product whitch is not expired.

#### Those Tables are protected by triggers observing illegal activity like deleting or updating.
#### If You are not interested in this solution skip next move, if You are, continue installation process.
- Create Table "Transactions_Deleted" and Trigger "Trigger_Delete"
- Create Table "Transactions_Update" and Trigger "Trigger_Update"
- Create Table "Table_Available_Orders" and insert into values

#### Every available command can be checked by:
  ```sql
           Select * from Table_Available_Orders
  ```

##  Fortuna-1-liga 
- Create table -> Matches, all tables with team lineups, Players, Match_Details in this order
- Bulk insert all ready tables, or insert Yours by:

#### Note: Every club has own code, like below. Wisła Kraków has numbers between 100 and 199.
#### It consists of: 1 - is number of the team, 30 - is ID of the player (not on a T-shirt) in this team.

 
  Example:
  
  ```sql
      INSERT INTO Players (ID_Player,ID_Team,Players_Name,Nr,Position,Date_Of_Birth)
      Values (130,'WisKra','Ángel Rodado',9,'Środkowy napastnik','1997-03-07')
  ```

- Insert every table of players to one table (Players)
- Create Procedures Insertion_Matches, Insert_Details

#### If you want to see the results of Fortuna 1 liga continue or skip this.
- Create table Wyniki_Excel
- Bulk insert Wyniki_Excel.csv
- Insert into Matches after, when you cleared and redid data from Wyniki_Excel

#### If you skipped last instruction use bottom expression, if not skip this. 


  Example:

  ```sql
      INSERT INTO Matches (Match,Home,Goal_Home,Goal_Away,Away,Match_Date,Round)
      Values ('WisKra vs PolWar','WisKra', 5, 0, PolWar, '2023-07-01 17:30', 30)
  ```
- Create View Goals_Table. Now you can see total points, wins, draws and losses
- Create View Table_Rounds_Goal. Now you can see a table counting a round (Matches), goals for and against.
- Create View Final_Table. This view join last two views and for final table, series of last matches left to be added.
- Create View Team_Series then Full_Series. Now you can see last five rounds.
- Finally Create View Tabela_Ostateczna_plus_series and now you have full view.
- If you want to see the view of home and away table Create View Goal_Home, Final_Table_Home and Goals_Away, Final_Table_Away.

#### Matches details
- Create Procedure Details
- Create View Classification_1out_of2, Classification_2out_of2, Classification

#### Below you can see how race looked to promotion to Ekstraklasa (Highest Polish division) - Wisła Kraków vs. Top 6
![Chart with points](https://github.com/Chopin1983/Fortuna-1-Liga/blob/main/wisla-and-top-6-2025-05-09T11-02-51.088Z.jpg)
![Chart with goals](https://github.com/Chopin1983/Fortuna-1-Liga/blob/main/wisla-and-top-6-goals-2025-05-09T11-03-21.292Z.jpg)

#### This is the end. Every available command you can see directly in the project

##  Mapa Polski
- Create tables Time and Distance
- Bulk insert MapCzas2.csv and MapDistance2.csv
- Create views TimeView and DistanceView
- Finaly Create Procedure Map and that's all

#### To find your way, use this simple execution

  Example:

```sql
       exec Map 3, Kraków, Białystok
```


## Next step
- Project is not finished, my next step will be.... (I'm hoping for some advice) :)
- Thx for reading this
