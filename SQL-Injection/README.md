# SQL Injection (SQLi)

**Learning resource:** [PortSwigger Web Security Academy — SQL injection](https://portswigger.net/web-security/sql-injection)  
**Status:** In progress  
**Lab write-ups:** To be added after I complete each lab.

## What is SQL injection?

SQL injection occurs when an application includes untrusted input in a database query in a way that lets the input change the query's intended structure or behavior. Depending on the context and database permissions, this can expose data, bypass application logic, or modify data.

The underlying issue is unsafe query construction—not simply the presence of unusual characters in a request.

## What I am learning

- How applications use SQL queries to retrieve or change data.
- How to identify user-controlled input that may influence a database query.
- How to inspect HTTP requests and responses with Burp Suite.
- How to form and test hypotheses methodically in a training lab.
- How to distinguish a confirmed vulnerability from an inconclusive result.
- How to describe impact and recommend an appropriate fix.

## Lab tracker

I will update this table as I work through the official labs. A lab will be marked **Solved** only after I complete it myself.

| Lab | Status | Notes |
|---|---|---|
| SQL injection vulnerability in WHERE clause allowing retrieval of hidden data | Not started | |
| SQL injection vulnerability allowing login bypass | Not started | |

[Browse all SQL injection labs](https://portswigger.net/web-security/sql-injection)

## Investigation workflow

1. **Understand the feature:** Browse the lab normally and identify where the application accepts input.
2. **Inspect traffic:** Use Burp Proxy and HTTP history to understand the relevant request and response.
3. **Identify a hypothesis:** Consider whether the input may affect a database query and what evidence would support that idea.
4. **Test carefully:** Use Burp Repeater to vary one input at a time, following the lab's objective.
5. **Compare results:** Look for meaningful differences in status codes, response content, behavior, or errors. A difference alone is not proof.
6. **Explain the cause:** Describe how the application's query construction allows the behavior.
7. **Record the lesson:** Capture the approach, evidence, impact, and mitigation in my own words.

## Root cause and remediation

A primary defence is to use **parameterized queries (prepared statements)** so user input is treated as data rather than executable SQL syntax. Depending on the application, additional good practices include:

- Avoid building SQL statements by concatenating untrusted input.
- Use safe, allow-listed handling for query parts that cannot be parameterized, such as selected sort fields.
- Apply least-privilege permissions to database accounts.
- Handle errors safely and avoid exposing unnecessary database details.
- Use testing and code review to verify that database access is implemented safely.

Input validation and hiding error messages can be useful supplementary controls, but they are not substitutes for parameterized queries.

## Notes from completed labs

*No labs documented yet. I will add my own observations after completing them.*

For each write-up, I plan to include:

- **Objective**
- **Vulnerability concept**
- **Methodology**
- **Relevant HTTP observations** (with secrets and tokens removed)
- **Root cause**
- **Potential impact**
- **Remediation**
- **Key takeaways**

## References

- [PortSwigger: SQL injection](https://portswigger.net/web-security/sql-injection)
- [PortSwigger: SQL injection cheat sheet](https://portswigger.net/web-security/sql-injection/cheat-sheet)
- [PortSwigger: Burp Suite documentation](https://portswigger.net/burp/documentation)

---

*These notes are for learning in authorized training environments. Any testing outside a lab must be explicitly authorized and within the target's permitted scope.*
