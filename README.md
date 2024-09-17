[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/r-tQZu0l)
# BBT3104-Lab1of6-DatabaseTransactions


| **Key**                                                               | Value                                                                                                                                                                              |
|---------------|---------------------------------------------------------|
| **Group Name**  C2                                                             | ? |
| **Semester Duration**                                                 | 19<sup>th</sup> August - 25<sup>th</sup> November 2024                                                                                                                       |

## Flowchart

## Pseudocode

```pseudo
START TRANSACTION
SET @orderNumber = (MAX(orderNumber) + 1) FROM orders
INSERT INTO orders (@orderNumber, currentDate, requiredDate, shippedDate, status, customerNumber)
SAVEPOINT before_product_1
INSERT INTO orderdetails (orderNumber, productcode, quantityOrdered, priceEach, orderLineNumber)
UPDATE products SET quantityInStock = quantityInStock - orderedQuantity
SAVEPOINT before_product_2
INSERT product_2
IF error THEN
  ROLLBACK TO SAVEPOINT before_product_2
ENDIF
INSERT remaining products
RECEIVE payment from customer
COMMIT TRANSACTION
```

## Support for the Sales Departments' Report
The following changes can be made:
1. Add a "payments" relation to store payment details for each order, including payment amounts, dates, and statuses (e.g., "Partial" or "Full").
2. Modify the "orders" relation to include "total_amount" and "amount_paid" columns. These will track the total amount of each order and how much has been paid so far.
3. Calculate outstanding balances by subtracting the "amount_paid" from "total_amount" for each order, in order to identify the unpaid balances.
4. Generate a report by querying the orders with unpaid balances and payment details to help the sales team follow up with clients.

