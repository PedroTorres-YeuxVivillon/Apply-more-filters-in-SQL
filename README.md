# 🗃️ SQL Filters: Working with Dates, Times, and Numeric Ranges

This repository documents my continued journey in learning SQL, focusing on using operators to filter numeric and date/time data. These skills are essential for security analysis, such as investigating incidents within specific timeframes.

## 📖 Project Overview

In this lab, I stepped into the role of a security analyst investigating a recent security incident. The goal was to analyze database login attempts by filtering for specific dates, times, and event IDs to pinpoint suspicious activity.

The key operators I practiced were:
*   **Comparison Operators:** `=`, `>`, `<`, `>=`, `<=`, `<>`
*   **Range Operator:** `BETWEEN | AND `

### **Skills Demonstrated**

*   Filtering records based on specific dates.
*   Creating date ranges to narrow search results.
*   Filtering records based on time values.
*   Using numeric comparisons and ranges to filter data.
*   Selecting specific columns to return cleaner results.

## 🛠️ Lab Tasks & My Solutions

The lab involved querying a single table: `log_in_attempts`.

### **Task 1: Login Attempts After a Certain Date**

**Goal:** Find all login attempts made after `2022-05-09` to investigate the incident.

**My Solution:**
I used the `>` operator to find logins strictly after the given date.
```sql
SELECT * 
FROM log_in_attempts 
WHERE login_date > '2022-05-09';
```

**Result:** This query returned 125 login attempts.

**Follow-up Goal:** Expand the search to include the incident date itself (2022-05-09).

**My Solution:**
I used the >= operator to include the specified date.

```sql
SELECT * 
FROM log_in_attempts 
WHERE login_date >= '2022-05-09';
```

**Result:** This broader query returned 165 login attempts.

### **Task 2: Narrowing the Search with a Date Range**

**Goal:** Focus the investigation on a specific window: login attempts between 2022-05-09 and 2022-05-11.

**My Solution:**
I used the BETWEEN and AND operators to define a clear, inclusive date range.

```sql
SELECT * 
FROM log_in_attempts 
WHERE login_date BETWEEN '2022-05-09' AND '2022-05-11';
```
**Result:** This precise query returned 123 login attempts within the target date range.

### **Task 3: Investigating Logins by Time**

**First Goal:** Identify logins made before the typical work start time of 07:00:00 to find potentially anomalous activity.

**My Solution:**
I filtered the login_time column using the < operator.

```sql
SELECT * 
FROM log_in_attempts 
WHERE login_time < '07:00:00';
```
**Finding:** The username in the fifth record of these early logins was eraab.

**Second Goal:** Refine the search to a specific one-hour window between 06:00:00 and 07:00:00.

**My Solution:**
I combined the BETWEEN operator with time values.

```sql
SELECT * 
FROM log_in_attempts 
WHERE login_time BETWEEN '06:00:00' AND '07:00:00';
```

**Finding:** The earliest login attempt in this window was at 06:01:31.

### **Task 4: Filtering by Event ID**

**First Goal:** Retrieve a simplified list of login attempts with an event_id of 100 or greater, showing only the event_id, username, and login_date.

**My Solution:**
I used SELECT to choose specific columns and >= for the numeric filter.

```sql
SELECT event_id, username, login_date 
FROM log_in_attempts 
WHERE event_id >= 100;
```
**Finding:** The login date for the third result in this set was 2022-05-09.

**Second Goal:** Further narrow the results to event IDs between 100 and 150.

**My Solution:**
I applied a numeric range filter using BETWEEN.

```sql
SELECT event_id, username, login_date
FROM log_in_attempts 
WHERE event_id BETWEEN 100 AND 150;
```

**Finding:** The username of the seventh result in this highly specific range was tmitchel.

### **✅ Conclusion** 

This lab was an excellent practical application of filtering with numbers and dates. I successfully learned how to:

- Use comparison operators (>, >=, <) to filter dates and numbers.
- Implement the BETWEEN ... AND ... operator to define precise ranges for dates, times, and numeric IDs.
- Write more efficient queries by selecting only the necessary columns.

  
