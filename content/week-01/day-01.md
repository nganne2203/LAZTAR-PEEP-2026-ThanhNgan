
+++
title = "Day 01 - 15/09/2026 (On-site)"
weight = 1
+++

# Daily Report - Day 01

## 1. Today's learning goals

Today I started getting familiar with Git and GitHub, focusing on basic operations for source code management and teamwork. I want to clearly understand the fundamentals such as initializing a repo, committing, pushing, pulling, merging, stashing, and handling conflicts.

## 2. What I did today

- Initialized a Git repository using `git init`.
- Cloned a repository from GitHub to my computer using `git clone`.
- Practiced creating files and staging changes using `git add`.
- Created a new commit with `git commit -m "..."`.
- Pushed code to GitHub using `git push`.
- Checked repository status with `git status`.
- Added a remote using `git remote add origin ...`.
- Practiced `git pull`, `git merge`, `git stash`, `git fetch` and `git stash list`.
- Learned and handled conflict situations during branch merging.

## 3. Knowledge gained

- Git is an essential version control tool in software development.
- `git init` is used to create a new repository.
- `git add` moves changes into the staging area before committing.
- `git commit` saves the current state of the project.
- `git push` uploads local changes to the remote repository.
- `git pull` syncs the latest remote updates to the local repository.
- `git merge` combines changes from another branch.
- `git stash` is useful for temporarily saving work without committing.
- When a merge has conflicts, they must be resolved manually before continuing.

## 4. Resolving Git conflicts

A conflict occurs when Git cannot decide which change to keep, usually because two branches changed the same part of a file. I used this workflow:

1. Run `git status` to identify conflicted files.
2. Open each file and review the `<<<<<<<`, `=======`, and `>>>>>>>` markers to distinguish the current branch's change from the incoming change.
3. Choose one change or combine both changes, then remove all conflict markers.
4. Review the code and mark the file as resolved with `git add <file-name>`.
5. Finish the operation in progress:
   - Merge: `git commit` or `git merge --continue`.
   - Rebase: `git rebase --continue`.
   - Cherry-pick: `git cherry-pick --continue`.

If I decide not to continue, I can return to the previous state with `git merge --abort`, `git rebase --abort`, or `git cherry-pick --abort`. Before completing the operation, I should run the relevant tests or review the edited file to avoid retaining an incorrect change.

## 5. Challenges encountered

- At first, I was confused between `git add`, `git commit`, and `git push`.
- During merge and cherry-pick operations, I had to read the error carefully and handle each conflict carefully instead of rushing to commit.
- I need more practice to remember the exact sequence of commands and their purposes.

## 6. Conclusion

Today was a very useful Git practice session. I learned important commands and how to work with a repository. Repeating these practices regularly will help me become more confident and proficient in future projects.

## 7. Visual notes from the learning process

![Git init](/images/reports/day-01/git-init.png)

![Git clone](/images/reports/day-01/git-clone.png)

![Git commit](/images/reports/day-01/git-commit.png)

![Git merge](/images/reports/day-01/git-merge.png)

![Git pull](/images/reports/day-01/git-pull.png)

![Git stash](/images/reports/day-01/git-stash.png)

![Git status](/images/reports/day-01/git-status.png)

![Git remote](/images/reports/day-01/git-remote.png)

![Git fetch](/images/reports/day-01/git-fetch.png)

## 8. Personal evaluation

I need to keep practicing and memorizing Git commands according to their specific use cases. This is a crucial foundation for future learning and projects, so I will spend more time reviewing it every day.
