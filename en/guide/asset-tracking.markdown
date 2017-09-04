---
title: Asset Tracking and Deployment Items
index: 2000
---

Tracking assets is a Clarive file shipping feature that checks whether the file that currently resides on a server is
the file actually shipped by Clarive.

There are three different use cases in Clarive where auditing can be activated:

### Overwrite Safety System

Before deploying an asset that will overwrite another, check whether the version of the asset we are overwriting is the
current version Clarive deployed in an earlier deployment job.

The reason for this is to make sure that no unintended assets (modified externally due to legitimate, exceptional
reasons) are overwritten inadvertently by a Clarive-initiated application deployment.

### Asset Auditing

This is a scheduled (nightly, hourly, etc.) or triggered audit executed by Clarive of tracked assets for given
environments or applications.

Drift or discrepancies detected during this audit can trigger emails or other Clarive operations.

### Manual Auditing

Track managed assets on request by a User. This can be achieved using the Resource action menu to run a `Verify Tracked
Asset` action for the selected asset.

## Activating Asset Tracking

### File Verification Method

Files are verified *on the target node* using one of two methods, if the connection is through the agent (or agentless).

- File checksum (MD5) value
- File date and size

File checksum requires the agent or target node to support a checksum operation. This may not be available for every
node. In which case, a combination of file size and file date will be used to uniquely identify the asset deployed. The
later verification method is not as trustworthy and may create false positives (i.e. Clarive mistakenly thinks the asset
is valid), although the probability is quitehigh (>99.9%) for most types of assets that both date and size work as
a good indicator that the asset matches.
