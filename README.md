This is a manifest for dotfiles and other scripts for quickly making a new
system like home and managing updates.

```
set -xe
git config --global user.email "foo@bar.com"
git config --global user.name "Vladislav Ivanishin"
cd
repo init -u git@github.com:ivladak/manifest.git --config-name
repo sync
repo forall -c 'git checkout $REPO_RREV'
repo init --config-name
set +xe
```

Further information can be found on the official
[git-repo](https://gerrit.googlesource.com/git-repo) page.

Short link to this readme (raw): https://bit.ly/3VUPV7A
