This is a manifest for dotfiles and other scripts for quickly making a new
system like home and managing updates.

```
set -xe
git config --global user.email ||
    git config --global user.email "foo@bar.com"
git config --global user.name ||
    git config --global user.name "Vladislav Ivanishin"
cd
repo init -u https://github.com/ivladak/manifest.git -b https --config-name
repo sync
repo forall -c 'git checkout $REPO_RREV'
repo init --config-name
set +xe
```

Further information can be found on the official
[git-repo](https://gerrit.googlesource.com/git-repo) page.

```
wget -O- https://raw.githubusercontent.com/ivladak/manifest/https/README.md |
    tee >(cat >&2) |
    sed -n '
        /^```/ {
            h;n
        }
        /^set +x/ {
            H;x;p;n;Q
        }
        H' | grep -v '^```' |
    bash -
```
