---
layout: post
title:  "Git WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! "
date:   2023-04-08 11:54:55 +0800
categories: ChatGPT
---

# Issue

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
SHA256:uxxxxxxx.
Please contact your system administrator.
Add correct host key in /Users/xxxx/.ssh/known_hosts to get rid of this message.
Offending RSA key in /Users/xxxx/.ssh/known_hosts:3
Host key for github.com has changed and you have requested strict checking.
Host key verification failed.
fatal: Could not read from remote repository.
```

# Solution
Copy above error into ChatGPT directly, then ChatGPT provide the solution:

This is a warning message that informs you that your SSH client has detected a different RSA key fingerprint than the one previously used to connect to the remote server. This could be due to the remote host's key being changed or your connection being intercepted by a man-in-the-middle attacker.

To avoid being attacked, the SSH client will refuse to connect to the host. If you're sure that the host is trustworthy, you can manually update the known_hosts file on your local machine to add or update the key fingerprint record for that host. Here are the steps:

1. Open a terminal or command prompt.
2. Run the following command:

   ```
   ssh-keygen -R github.com
   ```

   This command will remove the record for github.com from your known_hosts file.

3. Verify the RSA key fingerprint for github.com that you want to connect to:

   ```
   ssh-keyscan github.com
   ```

   This command will print the RSA key fingerprint for github.com. Copy this fingerprint.

4. Manually add the fingerprint to your known_hosts file:

   ```
   ssh-keygen -F github.com -l -E sha256 || ssh-keyscan -t rsa github.com >> ~/.ssh/known_hosts
   ```

   This command will add the RSA key fingerprint for github.com to your known_hosts file.

5. Try to connect to the remote server again.