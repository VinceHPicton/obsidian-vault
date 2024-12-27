Versioning is a feature that can be enabled or disabled at the **bucket level**.

Uploading under the **same key** (same file name basically) will update the version.

**Versioning is best practice**
- Protect against accidental deletes
	- If you delete a file, a "delete marker" is created, with a new version ID, to undo the delete you delete the delete marker.
- Easily rollback to older version

**Notes for exam**
- Any file not versioned prior to enabling will have verson "null"
- Suspending (disabling) versions will not delete old versions.
