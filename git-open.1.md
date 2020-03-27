# git-open - Open the repository's website in your browser.


## SYNOPSIS

`git open` [--issue] [--ci] [remote-name] [branch-name]


## DESCRIPTION

`git open` opens the repository's website in your browser. The major well known
git hosting services are supported.


## OPTIONS

```sh
# open git source page
git open
```

```sh
# open remote page
git open someremote
```

```sh
# open remote branch page
git open someremote somebranch
```

```sh
# open issue page
git open -i
```

```sh
# open ci/cd page
git open -c
```

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
git config [--global] option value
```

### GitLab options

To configure GitLab support (or other unique hosting situations) you may need to set some options.

`open.[gitdomain].domain`
  The (web) domain to open based on the provided git repo domain.

`open.[gitdomain].protocol`
  The (web) protocol to open based on the provided git repo domain. Defaults to `https`.

```sh
git config [--global] open.[gitdomain].domain [value]
git config [--global] open.[gitdomain].protocol [value]
```

**Example**

- Your git remote is at `ssh://git@git.internal.biz:7000/XXX/YYY.git`
- Your hosted gitlab is `http://repo.intranet/subpath/XXX/YYY`

```sh
git config [--global] "open.https://git.internal.biz.domain" "repo.intranet/subpath"
git config [--global] "open.https://git.internal.biz.protocol" "http"
```
