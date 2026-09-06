
#  SQL Query Writing Practice

## General instructions

- Write one complete and executable SQL query for each question.
- Use the table and field names exactly as provided.
- Use table-qualified field names in multi-table queries.
- Enclose text values in single quotation marks.
- Use parentheses to make mixed `AND` and `OR` logic explicit.
- Equivalent SQL syntax is acceptable when it produces the required result.
- The permitted SQL features are `SELECT`, `FROM`, `INNER JOIN`, `ON`, `WHERE`, `AND`, `OR` and `ORDER BY`.

---

# Practice Paper A

## Customer Order Analysis

**Recommended time:** 35 minutes  
**Total marks:** 25 marks

### Database structure

#### tblCustomer

| Field | Description |
|---|---|
| CustomerID | Primary key |
| CustomerName | Customer’s full name |
| State | VIC, NSW, QLD or SA |
| CustomerType | Corporate or Retail |

#### tblOrders

| Field | Description |
|---|---|
| OrderID | Primary key |
| CustomerID | Foreign key linked to tblCustomer.CustomerID |
| ProductID | Foreign key linked to tblProduct.ProductID |
| TotalPrice | Total order price |
| DeliveryStatus | Completed, Pending or Cancelled |

#### tblProduct

| Field | Description |
|---|---|
| ProductID | Primary key |
| ProductName | Name of the product |
| Category | Furniture, Technology or Stationery |
| StockStatus | In Stock or Back Order |

### Relationships

```text
tblCustomer.CustomerID = tblOrders.CustomerID
tblProduct.ProductID = tblOrders.ProductID
```
## Question 0 - 4 marks
Create the Table and insert the data from the above table into your own SQL database.

## Question 1 — 4 marks

A sales manager requires the customer name, order ID, and total price for completed orders priced at least $250.

Arrange the result from highest total price to lowest total price. When two orders have the same price, arrange them by customer name in ascending order.

Write one executable SQL query.

## Question 2 — 5 marks

Return `CustomerName`, `State`, `CustomerType`, `OrderID` and `TotalPrice` for orders that satisfy either of these alternatives:

- the customer is a VIC Corporate customer and the order is priced at least $180
- the customer is a NSW Retail customer and the order is priced at least $300

Arrange the result by state ascending, then total price descending, then customer name ascending.

Write one executable SQL query. Your Boolean grouping must preserve the two complete alternatives.

## Question 3 — 5 marks

A product analyst requires the order ID, product name, category and total price for completed orders priced at least $200 where the product belongs to either the Furniture category or the Technology category.

Arrange the result by category ascending. Within each category, arrange orders by total price descending. Use product name ascending to resolve equal prices.

Write one executable SQL query.

## Question 4 — 5 marks

Return `CustomerName`, `CustomerType`, `OrderID`, `DeliveryStatus` and `TotalPrice` for orders satisfying either of the following alternatives:

- the order is Pending and its total price is greater than $400
- the customer is Corporate, the order is Completed and its total price is exactly $300

Arrange the result by delivery status ascending, then total price descending, then customer name ascending.

Write one executable SQL query.

## Question 5 — 6 marks

A regional manager requires `CustomerName`, `State`, `CustomerType`, `ProductName`, `Category` and `TotalPrice`.

A row qualifies when all of the following requirements are satisfied:

- the order has a DeliveryStatus of Completed
- the order is priced at least $250
- the product belongs to either Furniture or Technology
- the customer satisfies either of these customer profiles:
  - VIC and Corporate
  - QLD and Retail

Arrange the result by state ascending, then customer type ascending, then total price descending, then customer name ascending.

Write one executable SQL query joining all three tables.

---

# Practice Paper B

## Student Submission Analysis

**Recommended time:** 35 minutes  
**Total marks:** 25 marks

### Database structure

#### tblStudent

| Field | Description |
|---|---|
| StudentID | Primary key |
| StudentName | Student’s full name |
| YearLevel | 11 or 12 |
| House | Blue, Gold, Green or Red |

#### tblSubject

| Field | Description |
|---|---|
| SubjectID | Primary key |
| SubjectName | Name of the subject |
| LearningArea | Computing, Mathematics, Science or Humanities |

#### tblSubmission

| Field | Description |
|---|---|
| SubmissionID | Primary key |
| StudentID | Foreign key linked to tblStudent.StudentID |
| SubjectID | Foreign key linked to tblSubject.SubjectID |
| Score | Score from 0 to 100 |
| SubmissionStatus | Submitted, Draft or Late |

### Relationships

```text
tblStudent.StudentID = tblSubmission.StudentID
tblSubject.SubjectID = tblSubmission.SubjectID
```

## Question 0 - 4 marks
Create the Table and insert the data from the above table into your own SQL database.

## Question 1 — 4 marks

Return the student name, subject name and score for Year 12 students whose submission status is Submitted and whose score is at least 80.

Arrange the result from highest score to lowest score. Use student name ascending to resolve equal scores.

Write one executable SQL query joining all three tables.

## Question 2 — 5 marks

Return `StudentName`, `YearLevel`, `House`, `SubjectName` and `Score` for submitted work scoring at least 70 where the student satisfies either of these profiles:

- Year 11 and Blue House
- Year 12 and Green House

Arrange the result by year level descending, then score descending, then student name ascending.

Write one executable SQL query.

## Question 3 — 5 marks

A curriculum leader requires the submission ID, student name, subject name, learning area and score for Submitted work scoring at least 75.

The subject must belong to either the Computing learning area or the Mathematics learning area.

Arrange the result by learning area ascending, then subject name ascending, then score descending, then student name ascending.

Write one executable SQL query.

## Question 4 — 5 marks

Return the student name, year level, subject name and score for Submitted work that satisfies either of these subject-specific standards:

- Data Analytics with a score of at least 70
- Software Development with a score of at least 85

Students from every year level and house may qualify.

Arrange the result by subject name ascending, then score descending, then student name ascending.

Write one executable SQL query. Ensure that the Submitted requirement applies to both subject-specific alternatives.

## Question 5 — 6 marks

A senior school coordinator requires `StudentName`, `YearLevel`, `House`, `SubjectName`, `SubmissionStatus` and `Score`.

A submitted assessment qualifies through either of the following pathways:

- the student belongs to Gold House, the subject is Data Analytics or Algorithmics, and the score is at least 80
- the student is in Year 12, the subject is Software Development, and the score is exactly 100

Arrange the result by subject name ascending, then score descending, then student name ascending.

Write one executable SQL query joining all three tables. Use parentheses to show the two pathways and the subject alternatives clearly.

---

# Extension Challenge

## Question 1 — 6 marks

Using the customer-order database from Practice Paper A, return `CustomerName`, `State`, `ProductName`, `Category`, `DeliveryStatus` and `TotalPrice`.

Include:

- every completed Technology order from a Corporate customer, regardless of state, when the total price is at least $300
- every completed Furniture order from a VIC customer, regardless of customer type, when the total price is at least $200

Arrange the result by category ascending, then state ascending, then total price descending, then customer name ascending.

Write one executable SQL query.

## Question 2 — 6 marks

Using the student-submission database from Practice Paper B, return `StudentName`, `YearLevel`, `House`, `SubjectName` and `Score`.

A row qualifies when the submission status is Submitted and either:

- the student is in Year 12 and scores at least 85 in a Computing subject
- the student belongs to Blue House and scores exactly 100 in a Mathematics subject

Arrange the result by learning area ascending, then score descending, then subject name ascending, then student name ascending.

Write one executable SQL query.
