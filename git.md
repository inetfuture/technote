# Must Done Configuration

```shell
git config --global user.name ???
git config --global user.email ???
git config --global core.editor vim
git config --global push.default simple
git config --global rerere.enabled true
git config --global alias.c checkout
git config --global alias.d diff
git config --global alias.dc "diff --cached"
git config --global alias.dw "diff --word-diff"
git config --global alias.l "log --all --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative"
git config --global alias.s status -sb
git config --global alias.reset-permission '!git diff -p -R --no-color | grep -E "^(diff|(old|new) mode)" --color=never | git apply'
```

# Books

- [Progit](https://github.com/progit/progit) **[MUST READ]** :bangbang:
- [Git Internals](https://github.com/pluralsight/git-internals-pdf)
- [Git Magic](http://www-cs-students.stanford.edu/~blynn/gitmagic/intl/zh_cn/)
- [Git Community Book 中文版](http://gitbook.liuhui998.com/)
- [gitready.com - learn git one commit at a time](http://gitready.com/)
- [GotGitHub - an open source E-book about GitHub in Chinese](https://github.com/gotgit/gotgithub)

# Blogs

- http://alblue.bandlem.com/Tag/git/

# Key Questions

- merge vs rebase
    - http://mislav.uniqpath.com/2013/02/merge-vs-rebase/
    - [Use gitk to understand git](http://lostechies.com/joshuaflanagan/2010/09/03/use-gitk-to-understand-git/)
- How merge works
    - http://www.quora.com/Git-revision-control/How-does-git-merge-work
    - http://codicesoftware.blogspot.com/2011/09/merge-recursive-strategy.html

# Best Practices

- [What's in a good commit](http://dev.solita.fi/2013/07/04/whats-in-a-good-commit.html) **[MUST READ]** :bangbang:
- [Colorful bash prompt reflecting git status](http://www.opinionatedprogrammer.com/2011/01/colorful-bash-prompt-reflecting-git-status/)
- [github-cheat-sheet](https://github.com/tiimgreen/github-cheat-sheet/blob/master/README.zh-cn.md)

# Work Flows

- https://www.atlassian.com/git/workflows
- [Understanding the Git Workflow](https://sandofsky.com/blog/git-workflow.html)
- [A Git Workflow for Agile Teams](http://reinh.com/blog/2009/03/02/a-git-workflow-for-agile-teams.html)
- [GitHub flow](http://scottchacon.com/2011/08/31/github-flow.html)
- [A successful Git branching model](http://nvie.com/posts/a-successful-git-branching-model/) **[MUST READ]** :bangbang:
    - [gitflow - Git extensions to provide high-level repository operations for Vincent Driessen's branching model](https://github.com/nvie/gitflow)
    - [git-flow cheatsheet](http://danielkummer.github.io/git-flow-cheatsheet/)

# Utilities

- [GIT utilities -- repo summary, repl, changelog population, author commit percentages and more](https://github.com/visionmedia/git-extras)
- [tig - Text-mode interface for git](https://github.com/jonas/tig)

# Platforms

- [gitlabhq - Project management and code hosting application](https://github.com/gitlabhq/gitlabhq)
- [gollum - A simple, Git-powered wiki with a sweet API and local frontend](https://github.com/gollum/gollum)

# Resource Collections

- [GitTips](https://gitcafe.com/riku/GitTips)

# Snippets

- Exclude files when git diff

    ```shell
    git diff oldBranch newBranch --name-only | egrep -v "(exclude1|exclude2)" | xargs git diff oldBranch newBranch --
    ```

# Sumup

Git is just a stupid content tracker.

It's used as a SCM, but not really designed as one.

Consider it as a file system.
