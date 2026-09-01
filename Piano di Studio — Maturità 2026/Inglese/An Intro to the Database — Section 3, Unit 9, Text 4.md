---
subject: inglese
tags:
  - inglese
  - database
  - maturita-2026
---
![[database_intro_study.svg|697]]

## What is a Database?

A **database** = a lot of data collected in some organised way.

The software used to access and manipulate it is called a **data manager**. The range of tasks a data manager can perform varies with the complexity of the program, but in general they all perform the following jobs:

---

## Key Structural Concepts

### Field

- A **single piece of data** (= one item of information)
- Similar to the **blank areas on a paper form**
- Can be defined as alphanumeric (text) or numeric (numbers)
- Can be limited to a certain length or specific values

### Record

- A **collection of data about a particular person, place, or thing**
- Individual items = fields, displayed in an onscreen form

### Table

- **Several records with the same fields**, displayed together
- Like a full form with many entries filled in

> **Field → Record → Table** (smallest to largest unit)

---

## What Databases Let You Do

### Queries

- Search for **subsets of data** that meet specified criteria
- **Retrieve data from different angles**
- **Sort and filter** the data

### Calculations

- Perform **mathematical calculations** on the data
- Perform **"if true" logic tests**
- Perform **"parse text"** operations (e.g. combining first and last names from two separate fields)

### Reports

- Present data in a **formatted, easy-to-read** output
- Can include calculations (e.g. combining data fields into one readable result)

---

## Two Types of Database Manager

### Flat-file database

- Manipulates only **one collection of data** (one table) **at a time**
- Designed for **simple, common operations**: searching and sorting
- Provides **ready-made tools and commands** — no programming needed
- Good for: basic use cases, single-user tasks

### Relational database

- Can **link data from several different tables**
- Managers define **relationships among common fields** across tables — called a **relational database**
- More powerful: includes **own programming or script languages** (e.g. **SQL**)
- Specialised applications designed for specific tasks
- Some can distinguish themselves from others (e.g. Oracle, MySQL, PostgreSQL)

> **Key distinction:** Flat-file = one table at a time. Relational = multiple linked tables.

---

## The Library Card Analogy

**Non-computerised database example:** Library card files (3×5-inch cards)

|Card set|Sorted by|
|---|---|
|Set 1|Title|
|Set 2|Author's name|
|Set 3|Subject matter|

**Problem:** One book = three cards = **terrible duplication of resources**.

**Computerised database advantage:** You only need **one set of records** — simpler and more efficient. You can search by title, name, or subject matter from the same record.

---

## Key Vocabulary

|Term|Meaning|Italian|
|---|---|---|
|**Database**|Organised collection of data|base di dati|
|**Data manager**|Software to access/manipulate a database|gestione dei dati|
|**Field**|Single piece of data (one blank on a form)|campo|
|**Record**|Full collection of data about one entity|record|
|**Table**|Multiple records with the same fields|tabella|
|**Query**|Search command to retrieve specific data|interrogazione|
|**Report**|Formatted, readable output of data|report|
|**Flat-file**|Single-table database|file sequenziale|
|**Relational**|Multi-table linked database|relazionale|
|**SQL**|Structured Query Language — common DB script language|—|
|**Patron**|Regular customer/user (e.g. library patron)|cliente abituale|