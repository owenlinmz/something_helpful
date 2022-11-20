# Change Git Author

## Step 1

Go to the particular repository and type command “git log”. You can see something like this in your terminal.

```sh
commit eea0b728959ab48af3fd75b828556fc1f9410c5c (HEAD -> master, origin/master, origin/HEAD)
Author: owenlinmz <linn2o@outlook.com>
Date:   Fri Nov 18 16:15:34 2022 +0800

    feat: add mvn deploy jar

commit a391cd7c5445b40a005bab04662220f4357cc1d5
Author: owenlinmz <linn2o@outlook.com>
Date:   Thu Oct 20 10:54:50 2022 +0800

    feat: add gradle2Maven py3 script

commit e257cb534b3a55b8bdd299a8fe8fed5704812068
Author: owenlinmz <linn2o@outlook.com>
Date:   Fri Nov 23 16:25:14 2018 +0800

    fix bug
```

## Step 2

If you want to change the last two commit, type `git rebase -i HEAD~2`

You can see

```sh
pick a391cd7 feat: add gradle2Maven py3 script
pick eea0b72 feat: add mvn deploy jar

# Rebase e257cb5..eea0b72 onto e257cb5 (2 commands)
#
# Commands:
# p, pick <commit> = use commit
# r, reword <commit> = use commit, but edit the commit message
# e, edit <commit> = use commit, but stop for amending
# s, squash <commit> = use commit, but meld into previous commit
# f, fixup [-C | -c] <commit> = like "squash" but keep only the previous
#                    commit's log message, unless -C is used, in which case
#                    keep only this commit's message; -c is same as -C but
#                    opens the editor
```

## Step 3

Insert the upon text like below, and then save by `:wq`.

```sh
exec git commit --amend --author="owenlinmz <linn2o@outlook.com>" -C HEAD
pick a391cd7 feat: add gradle2Maven py3 script
exec git commit --amend --author="owenlinmz <linn2o@outlook.com>" -C HEAD
pick eea0b72 feat: add mvn deploy jar
exec git commit --amend --author="owenlinmz <linn2o@outlook.com>" -C HEAD

# Rebase e257cb5..eea0b72 onto e257cb5 (2 commands)
#
# Commands:
# p, pick <commit> = use commit
# r, reword <commit> = use commit, but edit the commit message
# e, edit <commit> = use commit, but stop for amending
# s, squash <commit> = use commit, but meld into previous commit
# f, fixup [-C | -c] <commit> = like "squash" but keep only the previous
#                    commit's log message, unless -C is used, in which case
#                    keep only this commit's message; -c is same as -C but
#                    opens the editor
```

## Step 4

Check the author by `git log` again.
And you can see the author is changed.

## Step 5

Last, you can push force by `git push origin your-branch-name -f`.
