# Day 27

## Overview

Today's session focused on advanced SQL Injection techniques using **PortSwigger Web Security Academy**. Building upon the previous SQL Injection labs, I learned how attackers extract information from databases even when applications attempt to hide errors or suppress query results.

The labs introduced **UNION-based SQL Injection**, one of the most effective techniques for retrieving data from database tables, along with multiple forms of **Blind SQL Injection**, where attackers infer information without directly seeing query results.

One of the biggest takeaways from today's session was understanding that even if an application does not display database errors or query results, SQL Injection may still exist. Attackers can exploit response behavior, timing differences, and out-of-band communication to retrieve sensitive information.

These labs demonstrated why SQL Injection remains one of the most dangerous vulnerabilities in web applications and why secure coding practices are essential.

---

# Learning Objectives

Today's objectives were to:

- Understand UNION-based SQL Injection attacks.
- Determine the number of columns returned by SQL queries.
- Identify columns suitable for data extraction.
- Retrieve sensitive information from different database tables.
- Learn how multiple values can be extracted using a single column.
- Understand Blind SQL Injection.
- Perform conditional, error-based, and time-based SQL Injection.
- Learn Out-of-Band (OAST) SQL Injection techniques.

---

# What is UNION-Based SQL Injection?

The SQL **UNION** operator combines the results of two or more SELECT statements into a single result set.

If an attacker can inject a UNION query into a vulnerable application, they may retrieve information from completely different database tables than those intended by the application.

Instead of only viewing product information, an attacker may retrieve usernames, passwords, administrator accounts, email addresses, or other confidential records.

Because UNION queries return visible data directly to the application, they are considered one of the most powerful SQL Injection techniques.

---

# What is Blind SQL Injection?

Blind SQL Injection occurs when the application does not display database errors or query results.

Although attackers cannot directly view the extracted data, they can still determine information by observing how the application behaves after sending specially crafted requests.

Instead of reading the output, attackers rely on indirect indicators such as:

- Different page responses
- Response timing
- Server errors
- External interactions

Blind SQL Injection is slower than normal SQL Injection but is equally dangerous.

---

# Labs Completed

---

# 1. SQL Injection UNION Attack – Determining the Number of Columns

## Objective

Identify the number of columns returned by the original SQL query.

## Vulnerability

The application allowed additional SQL statements to be combined with the original query using the UNION operator.

However, the injected query must contain the same number of columns as the original query.

## What I Learned

Before retrieving database information, attackers first determine how many columns exist in the application's query.

Without matching the correct number of columns, the UNION attack fails.

This step is an important part of SQL Injection enumeration.

## Prevention

- Parameterized queries
- Prepared statements
- Input validation

---

# 2. SQL Injection UNION Attack – Finding a Column Containing Text

## Objective

Identify which database columns accept text values.

## Vulnerability

Although multiple columns existed, only certain columns were compatible with string data.

Attackers must identify these columns before extracting usernames, passwords, or other text-based information.

## What I Learned

Every SQL column has a specific data type.

Successful UNION attacks require matching both:

- Number of columns
- Data types

This lab highlighted the importance of understanding database schemas before attempting data extraction.

---

# 3. SQL Injection UNION Attack – Retrieving Data from Other Tables

## Objective

Retrieve sensitive information stored in unrelated database tables.

## Vulnerability

The SQL Injection vulnerability allowed additional SELECT statements to access completely different database tables.

Instead of returning only product information, the application exposed user-related data.

## What I Learned

Applications often restrict access at the user interface level but not at the database level.

If SQL Injection exists, attackers may access any table the database account has permission to read.

## Prevention

- Least privilege database accounts
- Parameterized queries
- Secure coding practices

---

# 4. SQL Injection UNION Attack – Retrieving Multiple Values in a Single Column

## Objective

Combine multiple database values into one visible output column.

## Vulnerability

Applications sometimes display only one column.

Attackers can combine several pieces of information into a single column to retrieve more data than intended.

## What I Learned

Even when applications limit displayed information, attackers may still extract multiple values using SQL functions.

This demonstrated the flexibility of UNION-based SQL Injection.

---

# 5. Blind SQL Injection with Conditional Responses

## Objective

Extract information by observing application responses.

## Vulnerability

The application never displayed database results directly.

Instead, attackers determined whether injected conditions were true or false by observing differences in webpage behavior.

## What I Learned

Blind SQL Injection relies on application logic instead of visible database output.

Even subtle response differences can reveal confidential information.

---

# 6. Blind SQL Injection with Conditional Errors

## Objective

Trigger database errors to extract information.

## Vulnerability

The application handled database errors differently depending on injected conditions.

Attackers could intentionally generate errors to determine whether specific statements evaluated to true.

## What I Learned

Error messages often reveal valuable information about database behavior.

Applications should never expose internal database errors to users.

---

# 7. Visible Error-Based SQL Injection

## Objective

Use detailed SQL error messages to gather database information.

## Vulnerability

The application displayed database errors directly in the browser.

These messages revealed valuable information about:

- Database type
- Query structure
- Table names
- Column names

## What I Learned

Verbose error messages significantly simplify SQL Injection exploitation.

Developers should log technical errors internally while presenting generic messages to users.

---

# 8. Blind SQL Injection with Time Delays

## Objective

Determine whether SQL conditions are true by measuring server response times.

## Vulnerability

Instead of displaying output, the database intentionally delayed its response when injected conditions evaluated to true.

## What I Learned

Time-Based Blind SQL Injection allows attackers to extract information even when:

- Errors are hidden
- Results are hidden
- Responses appear identical

Server timing becomes the communication channel.

---

# 9. Blind SQL Injection with Time Delays and Information Retrieval

## Objective

Retrieve actual database information using timing differences.

## Vulnerability

By repeatedly measuring response delays, attackers gradually reconstructed confidential information one character at a time.

## What I Learned

Although slow, Time-Based SQL Injection can eventually recover complete database contents.

Applications should never assume that hiding output prevents SQL Injection.

---

# 10. Blind SQL Injection with Out-of-Band Interaction

## Objective

Use external communication channels to retrieve database information.

## Vulnerability

The database was capable of making requests to external systems.

Instead of returning information through the application, data was transmitted using another communication channel.

## What I Learned

Out-of-Band SQL Injection is useful when:

- No errors are displayed
- Responses never change
- Timing attacks are ineffective

Although less common, OAST techniques are powerful against highly restricted applications.

---

# Important Concepts Learned

## UNION Operator

The UNION operator combines the results of multiple SELECT queries.

Attackers frequently abuse it to retrieve sensitive database records.

---

## Blind SQL Injection

Blind SQL Injection occurs when applications suppress errors and query results.

Information is extracted indirectly through:

- Boolean responses
- Timing
- Errors
- External communication

---

## Database Enumeration

Before extracting data, attackers identify:

- Number of columns
- Data types
- Table names
- Column names
- Database version

Enumeration is a critical phase of SQL Injection testing.

---

## Time-Based SQL Injection

Time-Based attacks use deliberate database delays to determine whether injected conditions evaluate to true or false.

Although slower than traditional SQL Injection, they remain highly effective.

---

## Out-of-Band SQL Injection

Out-of-Band SQL Injection uses external communication methods such as DNS or HTTP requests to retrieve information when direct responses are unavailable.

---

# Skills Practiced

- SQL Injection Testing
- UNION-Based SQL Injection
- Blind SQL Injection
- Database Enumeration
- Information Disclosure Testing
- Burp Suite
- SQL Query Analysis
- Secure Coding Awareness
- Web Application Security

---

# Tools Used

- Burp Suite Community Edition
- PortSwigger Web Security Academy
- Google Chrome Developer Tools

---

# Key Takeaways

- UNION attacks allow attackers to retrieve data from unrelated database tables.
- Successful UNION attacks require matching both the number and data types of columns.
- Blind SQL Injection remains dangerous even when applications hide database errors.
- Response timing and conditional logic can reveal sensitive information.
- Verbose database errors significantly increase application risk.
- Out-of-Band SQL Injection provides another method of extracting information when traditional techniques fail.
- Parameterized queries and prepared statements remain the most effective defense against SQL Injection.

---

# Conclusion

Today's labs demonstrated that SQL Injection extends far beyond bypassing login pages or retrieving visible records. Advanced techniques such as UNION attacks, Blind SQL Injection, Time-Based Injection, and Out-of-Band interactions allow attackers to extract sensitive information even when applications attempt to hide database responses.

By completing these exercises, I gained practical experience in database enumeration, information extraction, and advanced SQL Injection methodologies. These labs reinforced the importance of secure query construction, proper input validation, least-privilege database access, and comprehensive security testing to protect modern web applications from SQL Injection attacks.

---
