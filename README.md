# git-open

Type `git open` to open the repo website (GitHub, GitLab, Bitbucket) in your browser.

![Demo of git open in action](https://user-images.githubusercontent.com/39191/33507513-f60041ae-d6a9-11e7-985c-ab296d6a5b0f.gif)

## SYNOPSIS

```sh
$ git open` [--issue] [--ci] [remote-name] [branch-name]
```

## OPTIONS

```sh
# open git source page
$ git open
```

```sh
# open remote page
$ git open someremote
```

```sh
# open remote branch page
$ git open someremote somebranch
```

```sh
# open issue page
$ git open -i
```

```sh
# open ci/cd page
$ git open -c
```

## Installation

### Basic install

The preferred way of installation is to simply add the `git-open` script
somewhere into your path (e.g. add the directory to your `PATH` environment
or copy `git-open` into an existing included path like `/usr/local/bin`).

#### [Oh-My-Zsh](http://ohmyz.sh/)

1. `git clone git@github.com:luojinghui/git-open.git $ZSH_CUSTOM/plugins/git-open`
1. Add `git-open` to your plugin list - edit `~/.zshrc` and change
   `plugins=(...)` to `plugins=(... git-open)`
1. Reload source:`source .zshrc`

## SUPPORTED GIT HOSTING SERVICES

git-open can automatically guess the corresponding repository page for remotes
on the following git hosting services:

- github.com
- gitlab.com
- GitLab CE/EE (self hosted GitLab, see `CONFIGURATION`)

## CONFIGURATION

To configure git-open you may need to set some `git config` options. 
You can use `--global` to set across all repos, instead of just the current repo.

```sh
$ git config [--global] option value
```

### GitLab options

To configure GitLab support (or other unique hosting situations) you may need to set some options.

`open.[gitdomain].domain`
  The (web) domain to open based on the provided git repo domain.

`open.[gitdomain].protocol`
  The (web) protocol to open based on the provided git repo domain. Defaults to `https`.

```sh
$ git config [--global] open.[gitdomain].domain [value]
$ git config [--global] open.[gitdomain].protocol [value]
```

**Example**

- Your git remote is at `ssh://git@git.internal.biz:7000/XXX/YYY.git`
- Your hosted gitlab is `http://repo.intranet/subpath/XXX/YYY`

```sh
$ git config [--global] "open.https://git.internal.biz.domain" "repo.intranet/subpath"
$ git config [--global] "open.https://git.internal.biz.protocol" "http"
```

## Less is more
Super simple open method：

```sh
# config oh-my-zsh alias
$ alias go="git open"
```
then `go` anywhere...