---
title: Rule Quality Analysis
index: 5000
icon: rule
---

Rule Quality Analysis allows to check any rule for following the best practices. The best practices are grouped into
Policies, every one of them can be enabled/disabled separately. Some policies have advanced configuration.

# Quality Gate

Quality gate can be set to protect rules from saving if the Quality Analysis reports violations with severities that are
above the set level.

# Policies

There are currently six basic policies with a type five severity classification. The policies currently available are:

- **UnknownVariable** - reports the use of non-existent or unregistered variables. Severity: 5.
- **NotUsedVariable** - reports declared variables that are not in use. Severity: 2.
- **Complexity** - reports complex rules and operations. Severity: 3.
- **Deprecated** - reports deprecated operations. Severity: 4.
- **Rollback** - reports missing rollback logic. Severity: 5.
- **Miscellaneous** - reports the use of default naming of the palette operation. Severity: 1.


# Configuration

There are a number of configuration variables that allow for analysis configuration:

- `config.rules.critic.max_severity`: a rule may be stored if the severity of all policies not complied with is below
  the severity indicated.
- `config.rules.critic.policies`: policies to be analysed. Default all.

The actual policies may be configured. For *Complexity*:

- `config.rules.critic.policy.Complexity.max_code_lines`: maximum number of permitted lines of code
- `config.rules.critic.policy.Complexity.max_nesting_level`: maximum number of lines within a Server Code
- `config.rules.critic.policy.Complexity.max_operations_count`: maximum number of operations per rule
