# Subtle SQL Error: Implicit Type Conversion and NULL Values in Comparisons

This repository demonstrates a subtle SQL error that arises from implicit type conversion and the special handling of `NULL` values in comparisons.  The error is not immediately obvious and can be difficult to debug if not properly understood.

The `bug.sql` file contains the erroneous query.  The `bugSolution.sql` file provides a corrected version.

## Problem
The core issue lies in comparing a numeric column (`department_id`) with a string literal ('10'). While many databases will implicitly convert the string to an integer, this is problematic when dealing with `NULL` values. A comparison involving `NULL` typically returns `UNKNOWN`, which is treated as `false` in `WHERE` clauses. Therefore, rows where `department_id` is `NULL` are unintentionally omitted.

## Solution
The corrected query in `bugSolution.sql` explicitly handles `NULL` values using the `IS NULL` or `IS NOT NULL` operators and ensures that the data types in the comparison are consistent.
