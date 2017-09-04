---
title: EVAL
index: 5000
icon: statement-perl-eval
---

Run PERL code and trap run-time errors, assigning the return value to the [stash](/concepts/stash) variable data_key
(see op context menu from above) if defined.

In case of error, a message with the error is displayed and the rule fails.

Form to configure has the following field:

- **Code** - Text area to be filled with PERL instructions.
