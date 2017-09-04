---
title: cla migra - Migrations
index: 5000
icon: console
---

`cla migra`: Runs database migrations, which are needed to level the database version with the current version of
Clarive after upgrading or installing patches, features and plugins.

## Common flags

    --dry-run do not actually do anything, just print what's going to be done
    --init make sure migrations are initialized
    --yes answer yes to all questions
    --quiet be quiet
    --force do not perform safety checks

    --core run only core migrations
    --features run only features migrations
    --feature run only specific feature migrations
    --plugins run only plugins migrations
    --plugin run only specific plugin migrations

## Subcommands

### migra-state (default)

Prints the current state of the database.

### migra-init

Initializes the migrations.

### migra-reset

Resets the migrations.

### migra-start

Upgrade/Downgrade the migrations. Options are:

    --path path to migrations instead of default

### migra-downgrade

Downgrade to the specific version. Options are:

    --version the version to downgrade to
    --path path to migrations instead of default

### migra-set

Manually set the latest migrations version.

    --version the version to be set

### migra-fix

Removes the error from last migration. Use *ONLY* when the issue is really fixed.

### migra-oneshot

Upgrade/Downgrade manually by passing the migration version and method (upgrade by default). Options are:

    --version version of the migration
    --downgrade run downgrade instead of upgrade
