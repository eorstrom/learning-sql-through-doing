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
