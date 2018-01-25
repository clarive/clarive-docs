---
title: Docker
index: 5000
icon: docker
---

Docker administration panel gives you an easy and quick way to view and manage
docker Images / Containers inside your Clarive instance.

## Images

This section will list images added to your Clarive instance, you can delete any image by checking
that image and then click `Delete`

`Force Delete` option will force deleting images referenced in multiple repositories and
images being used by stopped containers, if an image has a running container, container must
be stopped before you can delete it.

If an image referenced by multiple repositories, list of repositories tagged will be listed
under `Tags` column, you can delete a single tag of that image by clicking on the `x` icon beside
it as you can see in the following image.

<img src="/static/images/docs/docker/image-tags.png" class="img_help" />

## Containers

This section will list all containers and their states, `running`, `exited`, and `created`, you can filter
by container state from the drop down `state filter` menu.

<img src="/static/images/docs/docker/state-filter.png" class="img_help" />

Also, you can filter containers by their id, name, and image id using the text search box.

<img src="/static/images/docs/docker/search-box.png" class="img_help" />

To take an action for a specific container first make sure to check it, then either `Start`,
`Stop`, `Delete` or `Force Delete`

<img src="/static/images/docs/docker/containers-actions.png" class="img_help" />

`Delete` option can't delete running containers, to delete a running container, either
`Force Delete` or stop the container then delete it.
