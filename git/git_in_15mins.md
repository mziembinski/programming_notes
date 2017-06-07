# Git in 15 minutes

## Workflow

> _check ["A successful Git branching model"](http://nvie.com/posts/a-successful-git-branching-model/ "Git branching model") link_

The central repo holds two main branches with an infinite lifetime:

* master
* develop

Creating a feature branch

```bash
git checkout -b myfeature develop
```

Incorporating a finished feature on develop 

```bash
git checkout develop
git merge --no-ff myfeature
git branch -d myfeature
git push origin develop
```

Creating a release branch 

```bash
git checkout -b release-1.2 develop
./bump-version.sh 1.2
git commit -a -m "Bumped version number to 1.2"
```

Finishing a release branch

```bash
git checkout master
git merge --no-ff release-1.2
git tag -a 1.2
git checkout develop
git merge --no-ff release-1.2
git branch -d release-1.2
```

For hotfix branches check the mentioned link.

## Common commands in my workflow

Nice log
```bash
git log --graph
```

Nicer log
```bash
git log --graph --full-history --all --color --pretty=format:"%x1b[31m%h%x09%x1b[32m%d%x1b[0m%x20%s"
```

similar but shotrer
```bash
git log --format=oneline
git log --graph --all --simplify-by-decoration
```

Another nicer log
```bash
git log --oneline --pretty='%C(red)%h%CresetI%C(yellow)%d%Creset%s%C(green)(%cr)%Creset'
```

Create aliases (e.g.for nice log)
```bash
git config alias.lg "log --oneline --pretty='%C(red)%h%CresetI%C(yellow)%d%Creset%s%C(green)(%cr)%Creset'"
git lg
```

2 diffs
```bash
git diff
git diff ..staged
```

Add and commit (without newly created)
```bash
git commit -am  "<commit message>"
```

## Reset

Just move HEAD
```bash
git reset --soft
```

Move HEAD + adjust working directory
```bash
git reset --hard
```

HEAD + index without working directory
```bash
git reset --mixed
```

2 steps back
```bash
git reset --hard^^
git reset --hard~2
```

## Not so common commands

```bash
git log master..myfeature
```

```bash
git rebase master
```

## For debugging

```bash
git bisect start head~5
git bisect run
```

## Low level commands

```bash
git show-ref
```

```bash
git cat-file -p [SHA part]
```

```bash
git ls-tree -r [SHA part]
```

## Great links

* [First Git cheatsheet](https://education.github.com/git-cheat-sheet-education.pdf "Github education")
* [Second but similar Git cheatsheet](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf "Github training")
* [Git tower cheatsheet](https://www.git-tower.com/blog/git-cheat-sheet/ "Git Tower")

* [A successful Git branching model I like](http://nvie.com/posts/a-successful-git-branching-model/ "Git branching model")
* [Nice tutorials collection](https://www.atlassian.com/git/tutorials "Atlassion tutorials")

* [Visualizing branch topology in git](https://stackoverflow.com/questions/1838873/visualizing-branch-topology-in-git) :notebook:

* [Nice Git GUI](https://www.gitkraken.com/)