---
name: GitHub push authentication
description: Secure authentication pattern for pushing this repository to GitHub.
---

For GitHub pushes, provide the secret through a temporary `GIT_ASKPASS` helper and disable terminal prompts. Do not put the token in the remote URL, git config, command output, or committed files.

**Why:** A direct bearer `http.extraHeader` push was rejected by the remote, while GitHub's username/password prompt flow with the same secret succeeded.

**How to apply:** Create the temporary helper only for the push, use `x-access-token` as the username, read the token from the environment for the password, and remove the helper immediately afterward.