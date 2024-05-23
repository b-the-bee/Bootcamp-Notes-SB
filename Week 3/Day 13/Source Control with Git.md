#data-science #data-engineering 

# Learning Objectives:
- Describe what source control is, and why we use it
- Add and commit features, and push to remote branches
- Create branches
- Create, review and merge pull requests
- Create a Git repository

## What is Source Control?
- Source control allows you to keep track of your files and every change made to them, ever.
- It also allows you to share these files and their change history with others, so they can make changes too.
## Git
- A distributed source control management system
- It has become the most widely used to manage source code nowadays

![[Pasted image 20240523114512.png]]

![[Pasted image 20240523115025.png]]

## Key Git components:
- **Working directory**: your private workspace, where changes are made. It may contain tracked and untracked files.
- **Staging area**: all changes you want to bundle up in the next commit (transaction) to your local repository.
- **Local repository**: your local version of the Git repository.

### Making changes in Git
![[Pasted image 20240523115352.png]]

## When should I commit?
Commits should:
- Pass all tests, and not have any known bugs to be fixed in a future commit
- Small self-contained changes that work
- Have short and meaningful commit messages
- Act as a save point for your code changes

### One important message about commits
**NEVER** commit sensitive information! This includes:
- Password
- Keys
- Private information about a person or entity
We can use handy tools like git-secrets to catch when we might accidentally commit sensitive information.


## When should I push?

- Code that isn't pushed exists only on your machine. So while it is a "save point" per commit, it's not backed up, and your team can't see it or use it. And if your machine crashes, it's still lost!
- Some teams like to push with every commit
- At least - do it when you leave your machine like lunchtime and at the end of the day.


## Sharing Git repositories
- Git is distributed, which means most of the changes happen in the people's indiviudal repositories, rather than a central location.
- Everyone's repos have all information about the repo.
- There is no "one and only" source of repo information.

- Git repos can be hosted in a private server, although this is something few people do.
- Most people prefer to utilise code hosting like BitBucket, SourceForge, GitLab or GitHub.

![[Pasted image 20240523143157.png]]

## Collaboration

We have gone through the clone, add and commit stages now. This is where collaboration starts:

```bash
$ git pull
$ git push
```

is what we used to pull the most recent remote changes, then push our commit.

