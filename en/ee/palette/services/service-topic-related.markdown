---
title: Load Topic Related
index: 5000
icon: service-topic-condition
---

This service stores in a stash variable information about topics that are related to another topic. This variable is
defined in `Return Key` field inside `Options` tab.

Form to configure has the following fields:

- **Name** - Allows the user to change the service name.
- **Mid** - Indicates the mid of the topic you want to load the related topics from. The use of variables is allowed
(e.g.: ${my_changeset} or in case the changeset is into stash: ${changesets[0].mid}).
- **Query type** - Indicates the type of relation between topics to be loaded and the one indicated by the field above.
- **Filter statuses** - Filters the related topics by selected statuses.
- **Not in statuses** - Makes the statuses filter work as an inverse filter. Statuses in `Filter statuses` will be
excluded.
- **Filter categories** - Filters the related topics by selected categories.
- **Depth** - Limits the depth of the search. For example, with depth 2, the service will load parent topics (level 1)
and parents of these too (level 2). We do not recommend to use a high value.
- **Single?** - Select it if you only want the topic with the lower `Mid` to be loaded (use filters to limit the
search).
- **Do not exclude event mid** - If checked, it also includes information about topic in the field `Mid` in the
indicated stash variable.
- **Mids only?** - Activate it to load only `Mid` of related topics. In some cases, it is convenient to select this
option to avoid loading a huge amount of information in stash.
