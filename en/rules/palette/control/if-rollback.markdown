---
title: IF ROLLBACK
index: 5000
icon: statement-if
---

Checks the status of rollback stash variable and process nested op if value match the value assigned to rollback key.

Data editor has the following key:

- **Rollback** - Rollback key, value column has to be filled with the desired boolean value, its default value is 1, so
  the rule will executed all nested ops if rollback is running.
