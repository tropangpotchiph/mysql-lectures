# MySQL WHERE

## Introduction to MySQL WHERE clause

When you use the SELECT statement to query data from a table, the order of rows in the result set is unspecified. To sort the rows in the result set, you add the ORDER BY clause to the SELECT statement.

The following illustrates the syntax of the ORDER BY clause:

```sql
SELECT
   select_list
FROM
   table_name
ORDER BY
   column1 [ASC|DESC],
   column2 [ASC|DESC],
   ...;
```

The search_condition is a combination of one or more expressions using the logical operator AND, OR and NOT.

In MySQL, a predicate is a Boolean expression that evaluates to TRUE, FALSE, or UNKNOWN.

The SELECT statement will include any row that satisfies the search_condition in the result set.

Besides the SELECT statement, you can use the WHERE clause in the UPDATE or DELETE statement to specify which rows to update or delete.

When executing a SELECT statement with a WHERE clause, MySQL evaluates the WHERE clause after the FROM clause and before the SELECT and ORDER BY clauses:

<img src="./images/where.png" alt="Where Flow" />

## MySQL WHERE clause examples

We’ll use the employees table from the sample database for the demonstration.

<img src="./images/employees.png" alt="Employees Table" />

## 1) Using MySQL WHERE clause with equality operator example

The following query uses the WHERE clause to find all employees whose job titles are Sales Rep:

```sql
SELECT
    lastname,
    firstname,
    jobtitle
FROM
    employees
WHERE
    jobtitle = 'Sales Rep';
```

In this example, the SELECT statement examines all rows of the employees table and selects only rows whose values in the jobTitle column are Sales Rep.

## 2) Using MySQL WHERE clause with the AND operator

The following example uses the WHERE clause to find employees whose job titles are Sales Rep and office codes are 1:

```sql
SELECT
    lastname,
    firstname,
    jobtitle,
    officeCode
FROM
    employees
WHERE
    jobtitle = 'Sales Rep' AND
    officeCode = 1;
```

In this example, the expression in the WHERE clause uses the AND operator to combine two conditions:

```sql
jobtitle = 'Sales Rep' AND officeCode = 1;
```

The AND operator evaluates to TRUE only if both expressions evaluate to TRUE. Therefore, the query returns rows whose values in the jobTitle column is Sales Rep and officeCode is 1.

## 3) Using MySQL WHERE clause with OR operator

This query finds employees whose job title is Sales Rep or employees who locate the office with office code 1:

```sql
SELECT
    lastName,
    firstName,
    jobTitle,
    officeCode
FROM
    employees
WHERE
    jobtitle = 'Sales Rep' OR
    officeCode = 1
ORDER BY
    officeCode ,
    jobTitle;
```

The OR operator evaluates to TRUE only if one of the expressions evaluates to TRUE:

```sql
jobtitle = 'Sales Rep' OR officeCode = 1
```

Therefore, the query returns any employee who has the job title Sales Rep or office code 1.

## 4) Using MySQL WHERE clause with the BETWEEN operator example

The BETWEEN operator returns TRUE if a value is in a range of values:

```sql
expression BETWEEN low AND high
```

The following query finds employees who locate in offices whose office code is from 1 to 3:

## TOPIC

```sql
SELECT
    firstName,
    lastName,
    officeCode
FROM
    employees
WHERE
    officeCode BETWEEN 1 AND 3
ORDER BY officeCode;
```

## 5) Using MySQL WHERE clause with the LIKE operator example

The LIKE operator evaluates to TRUE if a value matches a specified pattern.

To form a pattern, you use the % and _ wildcards. The % wildcard matches any string of zero or more characters while the _ wildcard matches any single character.

The following query finds the employees whose last names end with the string 'son':

```sql
SELECT
    firstName,
    lastName
FROM
    employees
WHERE
    lastName LIKE '%son'
ORDER BY firstName;
```

## 6) Using MySQL WHERE clause with the IN operator example

The IN operator returns TRUE if a value matches any value in a list.

```sql
value IN (value1, value2,...)
```

The following example uses the WHERE clause with the IN operator to find employees who locate in the office with office code 1.

## 7) Using MySQL WHERE clause with the IS NULL operator

To check if a value is NULL or not, you use the IS NULL operator, not the equal operator (=). The IS NULL operator returns TRUE if a value is NULL.

```sql
value IS NULL
```

---

**_NOTE:_** In the database world, NULL is a marker that indicates that a value is missing or unknown. And NULL is not equivalent to the number 0 or an empty string.

---

The following statement uses the WHERE clause with the IS NULL operator to get the rows with the values in the reportsTo column are NULL:

```sql
SELECT
    lastName,
    firstName,
    reportsTo
FROM
    employees
WHERE
    reportsTo IS NULL;
```

## 8) Using MySQL WHERE clause with comparison operators

The following table shows the comparison operators that you can use to form the expression in the WHERE clause.

| Operator | Description                                                            |
| -------- | ---------------------------------------------------------------------- |
| =        | Equal to. You can use it with almost any data type.                    |
| <> or != | Not equal to                                                           |
| <        | Less than. You typically use it with numeric and date/time data types. |
| >        | Greater than.                                                          |
| <=       | Less than or equal to                                                  |
| >=       | Greater than or equal to                                               |

The following query uses the not equal to (<>) operator to find all employees who are not the Sales Rep:

```sql
SELECT
    lastname,
    firstname,
    jobtitle
FROM
    employees
WHERE
    jobtitle <> 'Sales Rep';
```

The following query finds employees whose office code is greater than 5

```sql
SELECT
    lastname,
    firstname,
    officeCode
FROM
    employees
WHERE
    officecode > 5;
```

The following query returns employees with office code less than or equal to 4 (<=4):

```sql
SELECT
    lastname,
    firstname,
    officeCode
FROM
    employees
WHERE
    officecode <= 4;
```

## Summary

- Use the WHERE clause to filter rows by a condition.
- MySQL evaluates the WHERE clause after the FROM clause and before the SELECT and ORDER BY clauses.
