This is a manifest for dotfiles and other scripts for quickly making a new
system like home and managing updates.

```
grep -q github[.]com ~/.ssh/config ||
cat << EOF >> ~/.ssh/config

Host github.com
    HostName github.com
    IdentityFile ~/.ssh/github
EOF
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

wget -O- https://raw.githubusercontent.com/ivladak/manifest/main/README.md |
    tee >(cat >&2) |
    sed -n '/```/,/```/ p' |
    grep -v '```' |
    bash -
