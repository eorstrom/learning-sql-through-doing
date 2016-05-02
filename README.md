# learning-sql-through-doing

#####**1. Provide a query showing Customers (just their full names, customer ID and country) who are not in the US.**#####

```SQL
    SELECT 
    FirstNam|| " " ||LastName AS FullName, CustomerId, Country   
    FROM Customer   
    WHERE Country != 'USA';
```

#####**2. Provide a query only showing the Customers from Brazil.**#####

```SQL
    SELECT * FROM Customer   
    WHERE Country = 'Brazil';
```

#####**3. Provide a query showing the Invoices of customers who are from Brazil. The resultant table should show the customer's full name, Invoice ID, Date of the invoice and billing country.**#####

```SQL
    SELECT c.FirstName|| " " ||c.LastName AS FullName,   
    i.InvoiceId,   
    i.InvoiceDate,   
    i.BillingCountry   
    FROM Customer c   
    INNER JOIN Invoice i   
    ON c.CustomerID=i.CustomerID   
    WHERE c.Country = 'Brazil';
```

#####**4. Provide a query showing only the Employees who are Sales Agents.**#####
```SQL
    SELECT 
    * 
    FROM Employee e
    WHERE Title = 'Sales Support Agent';
```

#####**5. Provide a query showing a unique list of billing countries from the Invoice table.**#####

```SQL
    SELECT DISTINCT
    BillingCountry 
    FROM Invoice
    ORDER BY BillingCountry ASC;
```

#####**6. Provide a query that shows the invoices associated with each sales agent. The resultant table should include the Sales Agent's full name.**#####

```SQL
    SELECT
    i.invoiceId,
    e.FirstName|| " "||e.LastName as EmployeeName
    FROM Invoice i
    INNER JOIN Customer c ON c.CustomerId = i.CustomerId
    INNER JOIN Employee e ON e.EmployeeId = c.SupportRepId
    ORDER BY InvoiceId ASC;
```

#####**7. Provide a query that shows the Invoice Total, Customer name, Country and Sale Agent name for all invoices and customers.**#####

```SQL
      SELECT
      i.Total,
      i.BillingCountry,
      c.FirstName|| " " ||c.LastName AS CustomerName,
      e.FirstName|| " " ||e.LastName AS SalesAgentName
      FROM Invoice i
      INNER JOIN Customer c ON c.CustomerId = i.CustomerId
      INNER JOIN Employee e ON e.EmployeeId = c.SupportRepId;
```

#####**8. How many Invoices were there in 2009 and 2011? What are the respective total sales for each of those years?(include both the answers and the queries used to find the answers)**#####

```SQL
    Number of Invoices in 2009 : 83
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
```

#####**9. Looking at the InvoiceLine table, provide a query that COUNTs the number of line items for Invoice ID 37.**#####

```SQL
    SELECT Count(*) 
    FROM InvoiceLine il
    WHERE il.InvoiceId=37;
```

#####**10. Looking at the InvoiceLine table, provide a query that COUNTs the number of line items for each Invoice. HINT: GROUP BY**#####

```SQL
      SELECT InvoiceId, COUNT(InvoiceLineId) 
      FROM InvoiceLine
      GROUP BY InvoiceID;
```

#####**11. Provide a query that includes the track name with each invoice line item.**#####

```SQL
      SELECT 
      il.InvoiceId,
      t.Name
      FROM InvoiceLine il
      INNER JOIN Track t
      ON il.TrackId=t.TrackID
      ORDER BY il.InvoiceId ASC;
```

#####**12. Provide a query that includes the purchased track name AND artist name with each invoice line item.**#####

```SQL
    SELECT
    il.InvoiceLineId,
    t.Name,
    ar.Name
    FROM InvoiceLine il
    INNER JOIN Track t ON t.TrackId = il.TrackId
    INNER JOIN Album a ON a.AlbumId = t.AlbumId
    INNER JOIN Artist ar ON ar.ArtistId = a.ArtistId
    ORDER BY InvoiceLineId ASC;
```

#####**13. Provide a query that shows the # of invoices per country. HINT: GROUP BY**#####
 
```SQL
    SELECT
    Count(InvoiceId),
    BillingCountry 
    FROM Invoice
    GROUP BY BillingCountry;
```

#####**14. Provide a query that shows the total number of tracks in each playlist. The Playlist name should be included on the resulant table.**#####

```SQL
    SELECT
    COUNT(pt.TrackId),
    pt.PlaylistId,
    p.Name
    FROM PlaylistTrack pt
    INNER JOIN Playlist p ON p.PlaylistId = pt.PlaylistId
    GROUP BY p.PlaylistId;
```

#####**15. Provide a query that shows all the Tracks, but displays no IDs. The resultant table should include the Album name, Media type and Genre.**#####

```SQL
    SELECT
    t.Name AS TrackName,
    a.Title AS AlbumTitle,
    mt.Name AS MediaType,
    g.Name AS Genre
    FROM Track t
    INNER JOIN Album a ON a.AlbumId = t.AlbumId
    INNER JOIN MediaType mt ON t.MediaTypeId = t.MediaTypeId
    INNER JOIN Genre g ON g.GenreId = t.GenreId
    ORDER BY TrackName ASC;
```

#####**16. Provide a query that shows all Invoices but includes the # of invoice line items.**#####

```SQL

```

#####**17. Provide a query that shows total sales made by each sales agent.**#####

```SQL
    
```

#####**18. Which sales agent made the most in sales in 2009? HINT: MAX**#####



#####**19. Which sales agent made the most in sales over all?**#####



#####**20. Provide a query that shows the # of customers assigned to each sales agent.**#####



#####**21. Provide a query that shows the total sales per country. Which country's customers spent the most?**#####



#####**22. Provide a query that shows the most purchased track of 2013.**#####



#####**23. Provide a query that shows the top 5 most purchased tracks over all.**#####



#####**24. Provide a query that shows the top 3 best selling artists.**#####



#####**25. Provide a query that shows the most purchased Media Type.**#####
