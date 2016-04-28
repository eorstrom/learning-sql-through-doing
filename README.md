# learning-sql-through-doing

1. Provide a query showing Customers (just their full names, customer ID and country) who are not in the US.

  SELECT FirstName, LastName, CustomerId, Country 
  FROM Customer
  WHERE Country != 'USA';

2. Provide a query only showing the Customers from Brazil.

  SELECT FirstName, LastName, CustomerId, Country 
  FROM Customer
  WHERE Country = 'Brazil';

3. Provide a query showing the Invoices of customers who are from Brazil. The resultant table should show the customer's full name, Invoice ID, Date of the invoice and billing country.

  SELECT c.FirstName|| " " ||c.LastName AS FullName, 
  i.InvoiceId, 
  i.InvoiceDate, 
  i.BillingCountry
  FROM Customer c
  INNER JOIN Invoice i
  ON c.CustomerID=i.CustomerID
  WHERE Country = 'Brazil';

4. Provide a query showing only the Employees who are Sales Agents.

  SELECT 
  * 
  FROM Employee e
  WHERE Title = 'Sales Support Agent';

5. Provide a query showing a unique list of billing countries from the Invoice table.

  SELECT DISTINCT
  i.BillingCountry 
  FROM Invoice i
  ORDER BY BillingCountry ASC;

6. Provide a query that shows the invoices associated with each sales agent. The resultant table should include the Sales Agent's full name.

  SELECT 
  e.FirstName|| " " ||e.LastName AS FullName,
  c.SupportRepId,
  i.InvoiceId
  FROM Customer c
  INNER JOIN Employee e
  INNER JOIN Invoice i
  ON c.SupportRepId=e.EmployeeId
  ORDER BY InvoiceId ASC;

7. Provide a query that shows the Invoice Total, Customer name, Country and Sale Agent name for all invoices and customers.

  SELECT DISTINCT
  c.FirstName|| " " ||c.LastName AS CustomerName,
  c.Country,
  e.FirstName|| " " ||e.LastName AS SalesAgentName,
  i.Total,
  e.Title
  FROM Customer c
  INNER JOIN Employee e
  INNER JOIN Invoice i
  WHERE e.Title='Sales Support Agent'
  ORDER BY i.Total ASC;

8. How many Invoices were there in 2009 and 2011? What are the respective total sales for each of those years?(include both the answers and the queries used to find the answers)

Number of Invoices in 2009 - 83
  SELECT COUNT(*)
  FROM Invoice i
  WHERE InvoiceDate LIKE '2009%';

Total Sales for 2009: 446.46
  SELECT SUM(Total)
  FROM Invoice i;
  WHERE InvoiceDate LIKE '2009%';

Number of Invoices in 2011 - 83
  SELECT COUNT(*)
  FROM Invoice i
  WHERE InvoiceDate LIKE '2011%';

Total Sales: 469.58
  SELECT SUM(Total)
  FROM Invoice i
  WHERE InvoiceDate LIKE '2011%';

9. Looking at the InvoiceLine table, provide a query that COUNTs the number of line items for Invoice ID 37.
  
  SELECT Count(*) 
  FROM InvoiceLine il
  WHERE il.InvoiceId=37; 

10. Looking at the InvoiceLine table, provide a query that COUNTs the number of line items for each Invoice. HINT: GROUP BY

  SELECT COUNT(*) 
  FROM InvoiceLine
  GROUP BY InvoiceID;

11. Provide a query that includes the track name with each invoice line item.

  SELECT 
  il.InvoiceId,
  t.Name
  FROM Track t
  INNER JOIN InvoiceLine il
  ON il.TrackId=t.TrackID
  ORDER BY il.InvoiceId ASC;

12. Provide a query that includes the purchased track name AND artist name with each invoice line item.
 


13. Provide a query that shows the # of invoices per country. HINT: GROUP BY
 
  SELECT
  InvoiceId,
  BillingCountry 
  FROM Invoice
  GROUP BY BillingCountry;

14. Provide a query that shows the total number of tracks in each playlist. The Playlist name should be include on the resulant table.



15. Provide a query that shows all the Tracks, but displays no IDs. The resultant table should include the Album name, Media type and Genre.
16. Provide a query that shows all Invoices but includes the # of invoice line items.
17. Provide a query that shows total sales made by each sales agent.
18. Which sales agent made the most in sales in 2009? HINT: MAX
19. Which sales agent made the most in sales over all?
20. Provide a query that shows the # of customers assigned to each sales agent.
21. Provide a query that shows the total sales per country. Which country's customers spent the most?
22. Provide a query that shows the most purchased track of 2013.
23. Provide a query that shows the top 5 most purchased tracks over all.
24. Provide a query that shows the top 3 best selling artists.
25. Provide a query that shows the most purchased Media Type.
