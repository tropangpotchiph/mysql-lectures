# MySQL AND Operator

## Introduction to MySQL AND operator

MySQL doesn’t have a built-in Boolean type. Instead, it uses the number zero as FALSE and non-zero values as TRUE.

The AND operator is a logical operator that combines two or more Boolean expressions and returns 1, 0, or NULL:

```sql
A AND B
```

In this expression, A and B are called operands. They can be literal values or expressions.

The logical AND operator returns 1 if both A and B are non-zero and not NULL. It returns 0 if either operand is zero; otherwise, it returns NULL.

The logical AND operator returns 1 if both A and B are non-zero and NOT NULL. For example:

```sql
SELECT 1 AND 1;
```

The logical AND operator returns 0 if A or B is zero or both A and B are zero:

```sql
SELECT 1 AND 0, 0 AND 1, 0 AND 0, 0 AND NULL;
```

The logical AND operator returns NULL if either operand is non-zero or both operands are NULL.

```sql
SELECT 1 AND NULL, NULL AND NULL;
```

The following table illustrates the results of the AND operator when combining true, false, and null.

|       | TRUE  | FALSE | NULL  |
| ----- | ----- | ----- | ----- |
| TRUE  | TRUE  | FALSE | NULL  |
| FALSE | FALSE | FALSE | FALSE |
| NULL  | NULL  | FALSE | NULL  |

In practice, you’ll use the AND operator in the WHERE clause of the SELECT, UPDATE, DELETE statements to form a condition. Also, you can the AND operator in the conditions of the INNER JOIN and LEFT JOIN clauses.

When evaluating an expression that contains the AND operator, MySQL stops evaluating the remaining parts of the expression as soon as it can determine the result.

This is called short-circuit evaluation. In other words, the AND operator is short-circuited. For example:

```sql
SELECT 1 = 0 AND 1 / 0 ;
```

In this example, MySQL only evaluates the first part 1 = 0 of the expression 1 = 0 AND 1 / 0.

Since the expression 1 = 0 returns 0, MySQL can determine the result of the whole expression, which is 0.

Therefore, MySQL doesn’t need to evaluate the remaining part of the expression, which is 1/0; it would issue a division by zero error.

## MySQL AND operator examples

Let’s use the customers table in the sample database for the demonstration.

<img src="./images/customers.png" alt="" />

The following statement uses the AND operator to find customers who locate in California (CA), USA:

```sql
SELECT
    customername,
    country,
    state
FROM
    customers
WHERE
    country = 'USA' AND
    state = 'CA';
```

By using the AND operator, you can combine more than two Boolean expressions. For example, the following query returns the customers who locate in California, USA, and have a credit limit greater than 100K.

```sql
SELECT
    customername,
    country,
    state,
    creditlimit
FROM
    customers
WHERE
    country = 'USA' AND
    state = 'CA' AND
    creditlimit > 100000;
```

## Summary

- Use the AND operator to combine two Boolean expressions. The AND operator returns true when both expressions are true; otherwise, it returns false.
- Use the AND operator to form conditions in the WHERE clause of the SELECT statement.
