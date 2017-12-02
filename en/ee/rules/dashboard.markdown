---
title: Dashboard Rules
icon: rule
index: 1200
---

Dashboard rules is the way to define
global dashboards in the system.

They allow admins to take advantage of the full power of
rule control ops to customize Dashboard behaviour before
it's rendered to the user.

When editing Dashboard rules from the palette, under the folder **Dashlets**
there will be many different dashlets (or _widgets_) available
for dragging into the rule.

### The "Grid" System

The dashboard layout mechanism is based on the _grid system_,
popularized by web toolkits and libraries.

    |-----------------------------------------------------------|
    | 1  | 2  | 3  | 4  | 5  | 6  | 7  | 8  | 9  | 10 | 11 | 12 |
    |-----------------------------------------------------------|
    | 4-column dashlet  |           8-column dashlet            |
    |-----------------------------------------------------------|
    |  2-col  |  2-col  |  3-col       |   5-columns            |
    |-----------------------------------------------------------|
    |     4-column      |  x 2 rows    |   x 2-rows             |
    |-----------------------------------------------------------|

A grid system has 12 columns and unlimited rows.
Each dashlet can occupy from 1 to 12 columns and at least 1 row.

Here's a good explanation [in the Bootstrap library site](https://v4-alpha.getbootstrap.com/layout/grid/)
about how Bootstrap's grid system works.

When adding Dashlets

!!! todo
    The upcoming Clarive EE 7.2 release will include a visual
    dashboard (and form) designer. Stay tuned!

### Custom Dashboards

Although admins normally define dashboards as rules and assign them to user
roles, users can also customize these dashboards later.

Once the dashboard is rendered to the user, the
dashboard customization button on the top right
can be used to modify dashlet configuration.

When customizing dashboards, the user can access the
full dashlet configuration and change dashlet parameters.
Users can also remove dashlets and add new ones. User
changes are not reflected in the original Dashboard rule
and can only be viewed by the user that created it.

!!! warning
    Don't put any sensitive information in dashlet configuration.
    Users can see (and modify dashlets), so it's better to refrain
    from using information that can be manipulated by the user.
    This is specially true of the [HTML](/ee/palette/dashlets/html)
