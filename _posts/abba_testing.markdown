# What is an ABBA test?

I'm a big fan of the "complex code, simple SQL" pattern, where most complexity is written in a coding language that's optimized for testability, abstraction and modularity leaving 
us with only simple SQL queries to run and check. However, as a software developer working with big data, I'll often need to modify or build more complex SQL queries. In this case,
being able to quickly check if my query is doing what I want it to, and I haven't broken anything unexpected, is quite helpful. 

**_An ABBA test is a quick and dirty check that I sometimes use to ensure I haven't made a mistake or introduced a nasty surprise._**

## The Basic Structure

ABBA testing uses set logic to check that the results of two different queries are identical. If `A` is the set of rows that come back from the query I am building, and `B` 
is the set of rows I expect if my query is doing what I want it to, I can check that my query is working if I can prove the two sets are identical. An ABBA test checks this by proving
that A-B returns 0 rows and B-A returns 0 rows.

### A Simple Example

Let's write an ABBA test using the fizzbuzz problem. I want to write a query that will take in a table with a `number` column, and return the same table, with an additional `fizzbuzz`
column appended. The requirements for the `fizzbuzz` column are as follows:

1. If the `number` column contains a number that is divisible by 3, the `fizzbuzz` column should contain 'Fizz'
2. If the `number` column contains a number that is divisible by 5, the `fizzbuzz` column should contain 'Buzz'
3. If the `number` column contains a number that is divisible by 3 and 5, the `fizzbuzz` column should contain 'FizzBuzz'
4. Otherwise the `fizzbuzz` column should contain a varchar version of the original number.

In other words, given this input:
| number   |
| -------- |
| 1  | 
| 3 | 
| 5  | 
| 15 |

The query should give the following output:

| number   | fizzbuzz |
| -------- | --- |
| 1  | 1 |
| 3 | Fizz |
| 5  | Buzz|
| 15 | FizzBuzz |

The ABBA test I write while I build this query might look like the following:

```SQL
CREATE TABLE input as (
  SELECT 1 as number
  UNION
  SELECT 3 as number
  UNION
  SELECT 5 as number
  UNION
  SELECT 15 as number
);

CREATE TABLE expected_output as (
  SELECT 1 as number, '1' as fizzbuzz
  UNION
  SELECT 3 as number, 'Fizz' as fizzbuzz
  UNION
  SELECT 5 as number, 'Buzz' as fizzbuzz
  UNION
  SELECT 15 as number, 'FizzBuzz as fizzbuz
);

CREATE TABLE query as (
  SELECT
    number,
    CASE
      WHEN ( number % 3 == 0 AND number % 5 == 0 ) THEN 'FizzBuzz'
      WHEN number % 3 == 0 THEN 'Fizz'
      WHEN number % 5 == 0 THEN 'Buzz'
      ELSE CAST(number AS varchar)
    END as fizzbuzz
  FROM input
)

-- First, actual - expected:
SELECT number, fizzbuzz FROM query
EXCEPT ALL
SELECT number, fizzbuzz FROM expected_output

-- Then, expected - actual
SELECT number, fizzbuzz FROM expected_output
EXCEPT ALL
SELECT number, fizzbuzz FROM query
```


