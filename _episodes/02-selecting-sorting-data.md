---
title: Selecting and sorting data
teaching: 15
exercises: 5
keypoints:
- SQL is ideal for querying databases
- SQL queries have a basic query structure starting with `SELECT` field FROM table with additional keywords and criteria that can be used.
objectives:
- Understand how SQL can be used to query databases
- Understand how to build queries, using SQL keywords such as `DISTINCT` and `ORDER BY`
questions:
- What is a query?
- How do you query databases using SQL?
- How do you retrieve unique values in SQL?
- How do you sort results in SQL?
---

## What is a query?

A query is a question or request for data. For example, "How many journals does our library subscribe to?" When we query a database, we can ask the same question using a common language called Structured Query Language or SQL in what is called a statement. Some of the most useful queries - the ones we are introducing in this first section - are used to return results from a table that match specific criteria.

## Writing my first query

Let's start by opening DB Browser for SQLite and the imdb database (see Setup). Choose `Browse Data` and the `filmsAndSeries` table. The filmsAndSeries table contains columns or fields such as `title`, `type`, `description`, `release_year`, etc.

Let's write a SQL query that selects only the `title` column from the `filmsAndSeries` table.

```sql
SELECT title
FROM filmsAndSeries;
```
Note the order is important. First SELECT, then FROM.

If we want more information, we can add a new column to the list of fields right after `SELECT`:

```sql
SELECT Title, release_year
FROM filmsAndSeries;
```

Or we can select all of the columns in a table using the wildcard `*`.

```sql
SELECT *
FROM filmsAndSeries;
```

## Capitalization and good style

In the first query above, we have capitalized the words `SELECT` and `FROM` because they are SQL keywords. Even though capitalization makes no difference to the SQL interpreter, capitalization of these SQL terms helps for readability and is therefore considered good style. As you write and expand your own queries, it might be helpful to pick an option, such as [CamelCase](https://en.wikipedia.org/wiki/Camel_case), and use that style when naming tables and columns. Some tables and columns require capitalization and some do not. An occasional change of capitalization for these table and column names may be needed.

Example:

```
SELECT title
FROM filmsAndSeries;
```

instead of

```sql
SELECT Title
FROM filmsandseries;
```


## Comments
When the queries become more complex, it is good style to add comments to explain to yourself, or to others, what you are doing with your query. Comments help explain the logic of a section and provide context for anyone reading the query. It’s essentially a way of making notes within your SQL. In SQL, comments begin using -- and end at the end of the line. To mark a whole paragraph as a comment, you can enclose it with the characters /* and */. For example, a commented version of the above query can be written as:

```
-- We are only interested in the title
SELECT title
-- which we can find in the table filmsAndSeries
FROM filmsAndSeries
```

## Unique values

There may be a situation when you need to retrieve unique records and not multiple duplicate records. The SQL `DISTINCT` keyword is used after `SELECT` to eliminate duplicate records and fetch only unique records. Let's return all of the unique titles in a SQL query.

```sql
SELECT DISTINCT title
FROM filmsAndDatabases;
```

Note, some database systems require a semicolon `;` after each SQL statement. If we select more than one column, then the distinct pairs of values are returned.

```sql
SELECT DISTINCT title, release_year
FROM filmsAndSeries;
```

## Sorting

We can also sort the results of our queries by using the keyword `ORDER BY`. Let's create a query that sorts the articles table in ascending order by release_year using the `ASC` keyword in conjunction with `ORDER BY`.

```sql
SELECT *
FROM filmsAndSeries
ORDER BY release_year ASC;
```

The keyword `ASC` tells us to order it in ascending order. Instead, we can use `DESC` to get the descending order sorting by `tmdb_score`.

```sql
SELECT *
FROM filmsAndSeries
ORDER BY tmdb_score DESC;
```

`ASC` is the default, so by omitting `ASC` or `DESC`, SQLite will sort ascending (ASC).

We can also sort on several fields at once, in different directions. For example, we can order by `tmdb_score` descending and then `release_year` ascending in the same query.

```sql
SELECT *
FROM filmsAndSeries
ORDER BY tmdb_score DESC, release_year ASC;
```



> ## Challenge
> 
> Write a query that returns `Title`, `imdb_score`, `release_year` and `imdb_votes` from
> the filmsAndSeries table, ordered by the number of votes with the highest number first and alphabetically by title.
> > ## Solution
> > 
> > ```sql
> > SELECT title, imdb_score, release_year, imdb_votes
> > FROM filmsAndSeries
> > ORDER BY imdb_votes DESC, title ASC;
> > ```
> {: .solution}
{: .challenge}

