---
title: Introduction to SQL
teaching: 15
exercises: 0
objectives:
- Define a relational database.
- Explain what SQL is and why to use it.
questions:
- What is SQL?
- Why is SQL significant?
- What is the relationship between a relational database and SQL?
keypoints:
- SQL is a powerful language used to interrogate and manipulate relational databases.
---

## What is SQL?

**S**tructured **Q**uery **L**anguage, or SQL (sometimes pronounced "sequel"), is a powerful language used to interrogate and
manipulate relational databases. It is not a general
programming language that you can use to write an entire program. However, SQL
queries can be called from programming languages to let any program interact
with databases. There are several variants of SQL, but all support the
same basic statements that we will be covering today.

## Relational databases

Relational databases consist of one or more tables of data. These tables have
*fields* (columns) and *records* (rows). Every field has a data *type*. Every
value in the same field of each record has the same *type*. These tables can be
linked to each other when a field in one table can be matched to a field in another
table. SQL *queries* are the commands that let you look up data in a database or
make calculations based on columns.

Data types help
quality control of entries - you will receive an error if you try to enter a word
into a field that should contain a number. Understanding the nature of relational
databases, and using SQL, will help you in using databases in programming languages
such as R or Python.

## Why use SQL?

SQL is well established and has been around since the 1970s. It is still widely used
in a variety of settings.

SQL lets you keep the data separate from the analysis. There is no risk of
accidentally changing data when you are analysing it. If the data is updated,
a saved query can be re-run to analyse the new data.

SQL is optimised for handling large amounts of data. 

Many web applications (including WordPress and ecommerce sites like Amazon) run on a SQL (relational) database. Understanding SQL is the first step in eventually building custom web applications that can serve data to users.


## Database Management Systems

A database management system is a software tool that enables users to manage 
a database easily. It allows users to access and interact with the underlying data 
in the database. These actions can range from simply querying data to defining 
database schemas that fundamentally affect the database structure.

There are a number of different database management systems for working with
relational data. We're going to use SQLite today, but basically everything we
teach you will apply to the other database systems as well (e.g., MySQL,
PostgreSQL, MS Access, Filemaker Pro). The only things that will differ are the
details of exactly how to import and export data and possibly some differences in datatype.

## Introduction to DB Browser for SQLite

Let's all open the database we downloaded via the setup in DB Browser for SQLite.

You can see the tables in the database by looking at the left hand side of the
screen under Tables.

To see the contents of a table, click on that table and then click on the Browse
Data tab above the table data.

If we want to write a query, we click on the Execute SQL tab.


## Dataset Description

The data we will be using consists 4 tables of movie or series titles. 

**filmsAndSeries**

- Contains titles and metadataon movies and series from IMDB
- (12 fields, 5850 records)
- Field names: "id" , "title", "type", "description", "release_year", "age_certification", "runtime", "seasons", "imdb_score", "imdb_votes", "tmdb_popularity", "tmdb_score"

**productionCountries**

- country table which associates country codes with netflixid. 
- (2 fields, 6528 records)
- Field names: `id`, `Country`

**genres**

- Table which associates genres with id numbers. 
- (2 fields, 15080 records)
- Field names: `id`, `genre`

**countries**

- Table which associates a country name with a country code
- (2 fields, 248 records)
- Field names: code, country



## SQL Data Type Quick Reference

The main data types that are used in imdb database are `INTEGER` and `TEXT` which define what value the table column can hold.

Different database software/platforms have different names and sometimes different definitions of data types, so you'll need to understand the data types for any platform you are using.  The following table explains some of the common data types and how they are represented in SQLite; [more details available on the SQLite website](https://www.sqlite.org/datatype3.html).

| Data type              | Details                                                                                                                                                                                                                                                                         | Name in SQLite                                                                                                        | 
| :--------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-------------------------------------------------------------------------------------------------------------------- |
| boolean or binary      | this variable type is often used to represent variables that can only have two values: yes or no, true or false.                                                                                                                                                                | doesn't exist - need to use integer data type and values of 0 or 1.                                                   | 
| integer                | sometimes called whole numbers or counting numbers.  Can be 1,2,3, etc., as well as 0 and negative whole numbers: -1,-2,-3, etc.                                                                                                                                                | INTEGER                                                                                                               | 
| float, real, or double | a decimal number or a floating point value.  The largest possible size of the number may be specified.                                                                                                                                                                          | REAL                                                                                                                  | 
| text or string         | and combination of numbers, letters, symbols.  Platforms may have different data types: one for variables with a set number of characters - e.g., a zip code or postal code, and one for variables with an open number of characters, e.g., an address or description variable. | TEXT                                                                                                                  | 
| date or datetime       | depending on the platform, may represent the date and time or the number of days since a specified date.  This field often has a specified format, e.g., YYYY-MM-DD                                                                                                             | doesn't exist - need to use built-in date and time functions and store dates in real, integer, or text formats.  See [Section 2.2 of SQLite documentation](https://www.sqlite.org/datatype3.html#date_and_time_datatype) for more details. | 
| blob                   | a Binary Large OBject can store a large amount of data, documents, audio or video files.                                                                                                                                                                                        | BLOB                                                                                                                  | 


