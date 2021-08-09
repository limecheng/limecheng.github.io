# Solving Gitlab clone issue

# Problem description
- Gitlab was running at gitlab.some.domain
- Admin created "userA" with password "abc123"
- userA can login to Gitlab via web interface using password abc123
- userA creates a new repo "repoA" and follow the on-screen instruction
- The result was failure due to credential issues.

# What was checked
- verify password is correct by login to web interface
- reissue ssh key and make sure the user name in <cert>.pub residing in ~/.ssh/ is correct and matches that of user in Gitlab
- ssh -T gitlab.some.domain

# Solution
there's 2 ways to authenticate with Gitlab: SSH and HTTPS.

## SSH method

git remote add origin git@gitlab.some.domain:userA/flaskapp.git

## HTTPS method

git remote add origin https://userA@gitlab.some.domain:/userA/flaskapp.git

# Summary
In this case, the SSH method didn't work. HTTPS worked instead.
