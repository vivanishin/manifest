This is a manifest for dotfiles and other scripts for quickly making a new
system like home and managing updates.

```
cd
repo init -u git@github.com:ivladak/manifest.git --config-name
repo sync
repo forall -c 'git checkout $REPO_RREV'
```

Further information can be found on the official
[git-repo](https://gerrit.googlesource.com/git-repo) page.
