git submodule sync --recursive
- This updates your local `.git/config` submodule URLs to match what's currently in `.gitmodules`.
- It's useful if you've changed the remote URLs in `.gitmodules` (e.g., switching from SSH to HTTPS), but your local Git config hasn't picked up the changes.

THEN
git submodule update --init --recursive --force
- Ensures that each submodule is checked out at the **specific commit** that your main repo (the superproject) expects.
- Initializes submodules if they haven’t been cloned yet.
- Recursively updates nested submodules.
- Forces Git to discard local changes inside submodules and checkout the correct commit.

OR
git submodule sync --recursive && git submodule update --init --recursive --force