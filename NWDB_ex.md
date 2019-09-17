# SQL Queering Homework :taco:

Use your sequel sever to run the queries and come to an answer.
Pay attention to detail, as there is ONE right answer and following guidelines & or instructions is an important skill for consultants.

Note we will refer to Northwind Database as NWDB
Please read on.

**Important**
Your response should always be the **SQL query** + the short answer where appropriate.

## Queries

### Q1 - How many orders in NWDB?

Query: SELECT COUNT(*) FROM Orders

Response: 830


### Q2 - How many order that the Ship City is Rio de Janeiro?

Query: SELECT COUNT(*) FROM Orders
        WHERE ShipCity = 'Rio de Janeiro'

Response: 34

### Q3 - Select all orders that the Ship City is Rio de Janeiro or Reims?

Query: SELECT * FROM Orders
        WHERE ShipCity = 'Rio de Janeiro' OR ShipCity = 'Reims'

Response: 39 entries

### Q4 - Select all of the entries where the Company name has a z or a Z in the table of Customers

Query: SELECT * FROM Customers
        WHERE CompanyName LIKE '%z%'

Response: 6 entries

### Q5 - We need to update all of our FAX information! This Day and age it is a must! :sweat_smile::sweat_smile::sweat_smile: Find me the Name of All of the companies that we do not have their FAX numbers! I would also like to know with whom I need to speak with, their contact numbers and what city they are base in.

Query: SELECT CompanyName, ContactName, Phone, City, Fax FROM Customers
        WHERE Fax IS NULL

Response:

| CompanyName             | ContactName          | Phone          | City           | Fax  |
|-------------------------|----------------------|----------------|----------------|------|
| Antonio Moreno Taquería | Antonio Moreno       | (5) 555-3932   | México D.F.    | NULL |
| B's Beverages           | Victoria Ashworth    | (171) 555-1212 | London         | NULL |
| Chop-suey Chinese       | Yang Wang            | 0452-076545    | Bern           | NULL |
| Comércio Mineiro        | Pedro Afonso         | (11) 555-7647  | Sao Paulo      | NULL |
| Familia Arquibaldo      | Aria Cruz            | (11) 555-9857  | Sao Paulo      | NULL |
| Folk och fä HB          | Maria Larsson        | 0695-34 67 21  | Bräcke         | NULL |
| Godos Cocina Típica     | José Pedro Freyre    | (95) 555 82 82 | Sevilla        | NULL |
| Gourmet Lanchonetes     | André Fonseca        | (11) 555-9482  | Campinas       | NULL |
| Great Lakes Food Market | Howard Snyder        | (503) 555-7555 | Eugene         | NULL |
| Island Trading          | Helen Bennett        | (198) 555-8888 | Cowes          | NULL |
| Königlich Essen         | Philip Cramer        | 0555-09876     | Brandenburg    | NULL |
| Let's Stop N Shop       | Jaime Yorres         | (415) 555-5938 | San Francisco  | NULL |
| Morgenstern Gesundkost  | Alexander Feuer      | 0342-023176    | Leipzig        | NULL |
| Princesa Isabel Vinhos  | Isabel de Castro     | (1) 356-5634   | Lisboa         | NULL |
| Queen Cozinha           | Lúcia Carvalho       | (11) 555-1189  | Sao Paulo      | NULL |
| QUICK-Stop              | Horst Kloss          | 0372-035188    | Cunewalde      | NULL |
| Ricardo Adocicados      | Janete Limeira       | (21) 555-3412  | Rio de Janeiro | NULL |
| Richter Supermarkt      | Michael Holz         | 0897-034214    | Genève         | NULL |
| Save-a-lot Markets      | Jose Pavarotti       | (208) 555-8097 | Boise          | NULL |
| The Big Cheese          | Liz Nixon            | (503) 555-3612 | Portland       | NULL |
| Tortuga Restaurante     | Miguel Angel Paolino | (5) 555-2933   | México D.F.    | NULL |
| Wellington Importadora  | Paula Parente        | (14) 555-8122  | Resende        | NULL |

### Q6 - Ahh there you are! My prize :star::star:SPARTANTS:star::star:! MY MARES AND MY STALLIONS! We need to re-target all of our Customers is Paris! Get me information on these clients.

Query: SELECT * FROM Customers
        WHERE City = 'Paris'

Response:

| CustomerID | CompanyName          | ContactName       | ContactTitle      | Address                 | City  | Region | PostalCode | Country | Phone           | Fax             |
|------------|----------------------|-------------------|-------------------|-------------------------|-------|--------|------------|---------|-----------------|-----------------|
| PARIS      | Paris spécialités    | Marie Bertrand    | Owner             | 265, boulevard Charonne | Paris | NULL   | 75012      | France  | (1) 42.34.22.66 | (1) 42.34.22.77 |
| SPECD      | Spécialités du monde | Dominique Perrier | Marketing Manager | 25, rue Lauriston       | Paris | NULL   | 75016      | France  | (1) 47.55.60.10 | (1) 47.55.60.20 |

### Q7 - WAIT! Where are you going? (...) These clients are hard to sell too! We need more intel.. Can you find out, from these clients from Paris, whom orders the most by quantity? Who are our top 5 clients?  

Query: SELECT * FROM Orders
        WHERE ShipCity = 'Paris'

       SELECT * FROM Customers
        WHERE City = 'Paris'

       SELECT DISTINCT TOP 5 CustomerID FROM Orders

Response: Spécialités du monde orders the most from Paris (orderID = SPECD)
Top 5 clients are:

| CustomerID |
|------------|
| ALFKI      |
| ANATR      |
| ANTON      |
| AROUT      |
| BERGS      |

### Q8 - OMG What are you? Some kind of SQL Guardian Angel? THIS IS AMAZING! May God pay you handsomely :smile_cat: because I have no cash on me!..  I do have one more request. I need to know more about these these Paris client. Can you find out which ones their deliveries took longer than 10 days? Display the Business/client name, contact name, all their contact details (don't forget the fax!), as well as the number of deliveries that where overdue! Just add a column named: 'Number overdue orders'! simple, thank you!

Query: SELECT * FROM Orders
        WHERE ShippedDate - OrderDate > 10 AND ShipCity = 'Paris'

Response: There are no orders from paris that took longer than 10 days (?)
