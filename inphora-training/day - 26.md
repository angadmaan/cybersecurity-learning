# Day 26

## Overview

Today's session focused on applying the SQL Injection concepts learned previously through hands-on labs in **PortSwigger Web Security Academy**. The objective was to understand how attackers exploit insecure SQL queries to bypass authentication, retrieve hidden information, and enumerate database details.

Unlike the previous day, which introduced SQL Injection theoretically, today's labs demonstrated how small flaws in SQL query construction can expose sensitive information stored in databases. The exercises also introduced techniques for identifying different database management systems (DBMS) and extracting database schema information from Oracle, MySQL, and Microsoft SQL Server.

These labs reinforced the importance of secure coding practices such as parameterized queries and proper input validation.

---

# Learning Objectives

During today's labs, I learned how to:

- Identify SQL Injection vulnerabilities.
- Retrieve hidden database records.
- Bypass login authentication.
- Identify the underlying database management system.
- Extract database version information.
- Enumerate database tables and columns.
- Understand the differences between Oracle and non-Oracle databases.
- Analyze insecure SQL queries.

---

# What is SQL Injection?

SQL Injection (SQLi) is a web application vulnerability that allows an attacker to manipulate SQL queries by injecting malicious input into user-controlled fields.

When applications concatenate user input directly into SQL statements without proper validation or parameterized queries, attackers may change the logic of the query and gain unauthorized access to data.

---

# Why SQL Injection is Dangerous

A successful SQL Injection attack can allow an attacker to:

- Bypass authentication
- Read confidential information
- Modify existing records
- Delete database contents
- Enumerate database structure
- Access administrator accounts
- Execute administrative database commands

Because many organizations store sensitive customer information in databases, SQL Injection remains one of the most critical web security vulnerabilities.

---

# Labs Completed

---

# 1. SQL Injection in WHERE Clause Allowing Retrieval of Hidden Data

## Objective

Exploit a vulnerable product filtering feature to retrieve hidden database records.

## Vulnerability

The application inserted user-controlled input directly into the SQL WHERE clause without proper validation.

Instead of returning only publicly visible products, the manipulated query returned additional hidden records.

## What I Learned

The WHERE clause controls which records are returned by a query.

If attackers can manipulate this condition, they may retrieve confidential information that should never be displayed.

This lab demonstrated how SQL Injection can expose sensitive business data without requiring administrator privileges.

## Prevention

- Parameterized queries
- Prepared statements
- Input validation
- Principle of least privilege

---

# 2. SQL Injection Allowing Login Bypass

## Objective

Use SQL Injection to bypass the application's authentication mechanism.

## Vulnerability

The login page directly concatenated the supplied username and password into an SQL query.

By manipulating the input, the application's authentication logic was altered, allowing unauthorized access.

## What I Learned

Authentication systems are common targets for SQL Injection because successful exploitation may immediately provide administrative access.

I also learned that authentication should never depend on dynamically constructed SQL statements.

## Prevention

- Prepared statements
- Parameterized queries
- Secure authentication design
- Input validation

---

# 3. Querying Database Type and Version (Oracle)

## Objective

Identify the database server and retrieve version information.

## Vulnerability

The SQL Injection vulnerability allowed additional SQL queries to be executed, exposing information about the database system.

## What I Learned

Before extracting data, attackers often determine which database management system the application uses.

Different databases support different SQL syntax, functions, and system tables.

Knowing the database version helps attackers choose compatible techniques.

## Oracle Concepts Learned

- Oracle database structure
- Version identification
- System information queries
- Database fingerprinting

---

# 4. Querying Database Type and Version (MySQL & Microsoft SQL Server)

## Objective

Identify the underlying database platform.

## Vulnerability

The application failed to restrict SQL statements, allowing additional database information to be retrieved.

## What I Learned

Every database platform behaves differently.

MySQL, Microsoft SQL Server, PostgreSQL, and Oracle each use unique syntax and system tables.

Database fingerprinting is an important step during penetration testing because later exploitation depends on identifying the correct database.

---

# 5. Listing Database Contents on Non-Oracle Databases

## Objective

Enumerate tables and columns stored in the database.

## Vulnerability

SQL Injection allowed access to metadata describing the database structure.

## What I Learned

Modern databases maintain system tables that store information about:

- Tables
- Columns
- Views
- Schemas

By querying these metadata tables, attackers can discover valuable information without guessing table names.

Database enumeration is often the first step before extracting sensitive records.

## Prevention

- Restrict database permissions
- Prevent SQL Injection
- Hide unnecessary database metadata

---

# 6. Listing Database Contents on Oracle

## Objective

Enumerate database objects within Oracle.

## Vulnerability

Oracle stores metadata differently from other database systems.

Using SQL Injection, the application exposed information about existing tables and columns.

## What I Learned

Although every relational database stores metadata, Oracle uses different system views and naming conventions.

Understanding these differences helps security professionals identify vulnerable Oracle applications.

---

# Database Enumeration

Database enumeration is the process of discovering:

- Database names
- Tables
- Columns
- Data types
- Schemas

Attackers typically perform enumeration before attempting to extract confidential information.

Understanding database structure greatly increases the effectiveness of SQL Injection attacks.

---

# Database Fingerprinting

Before exploiting SQL Injection, attackers often identify the database management system.

Common databases include:

- Oracle Database
- MySQL
- Microsoft SQL Server
- PostgreSQL
- SQLite

Each platform has unique SQL syntax and internal structures.

Correctly identifying the DBMS allows attackers to use database-specific techniques.

---

# Secure Coding Practices

To prevent SQL Injection vulnerabilities, developers should:

- Use parameterized queries.
- Implement prepared statements.
- Validate user input.
- Apply least-privilege database accounts.
- Hide database error messages.
- Avoid dynamic SQL where possible.
- Perform regular security testing.
- Follow OWASP Secure Coding Guidelines.

---

# Skills Practiced

- SQL Injection Testing
- Authentication Bypass Analysis
- Database Enumeration
- Database Fingerprinting
- Burp Suite
- Web Application Security
- Secure Coding Awareness
- SQL Query Analysis

---

# Tools Used

- Burp Suite Community Edition
- PortSwigger Web Security Academy
- Browser Developer Tools

---

# Key Takeaways

- SQL Injection can expose much more than user data.
- Authentication pages are common SQL Injection targets.
- Database fingerprinting helps identify the underlying DBMS.
- Database enumeration reveals tables, columns, and schemas.
- Oracle and non-Oracle databases use different metadata structures.
- Prepared statements remain the most effective defense against SQL Injection.
- Proper input validation and least-privilege database permissions significantly reduce risk.

---

# Conclusion

Today's hands-on SQL Injection labs demonstrated how attackers move beyond simply identifying vulnerabilities to gathering valuable information about the target database. By exploiting insecure SQL queries, I learned how hidden records can be exposed, authentication mechanisms bypassed, and database structures enumerated across different database management systems.

These exercises reinforced that SQL Injection is not only a method for retrieving data but also a pathway to understanding an application's entire database architecture. The experience emphasized the importance of secure query construction, parameterized statements, and defense-in-depth when designing modern web applications.

---

