---
title: Snapshots
index: 5000
icon: slot
---

A *snapshot* captures the status of Clarive at a given point in time. In order to take a snapshot, go to the Admin menu,
then ![](/static/images/icons/slot.svg) Snapshots.

A snapshot may be taken by simply clicking ![](/static/images/icons/add.svg) Take snapshot and choosing a heading
together with the components you wish to store.

Once selected, the system will take the snapshot, which will appear in the table dimensioned to fit the snapshot.

You may delete the snapshot by clicking ![](/static/images/icons/delete.svg) or you may export it
![](/static/images/icons/export.svg). When exporting one or more rows, a *.zip*-compressed file containing the *yml*
files with the exported components is downloaded to the client.

You may import previously taken snapshot ![](/static/images/icons/import.svg). It is possible to import only part of the
snapshot selecting needed components.

It is also possible to take snapshots by means of rules, using the [service *Take System
Snapshot*](rules/palette/services/snapshot).
