# aw_rpi_ppa_repo

repo for some raspberry pi packages

## Install as a service that runs at boot

### Install the gpg key and then the repo

```bash
curl -s --compressed "https://jcksnvllxr80.github.io/aw_rpi_ppa_repo/KEY.gpg" | sudo apt-key add -
sudo curl -s --compressed -o /etc/apt/sources.list.d/my_list_file.list "https://jcksnvllxr80.github.io/aw_rpi_ppa_repo/my_list_file.list"
sudo apt update
```

### Install the service

```bash
sudo apt install mypackage
```

### Updating the mypackage service

```bash
apt install --only-upgrade mypackage
```

### Uninstall the service

```bash
sudo apt remove mypackage -y
```

### Starting, stopping, restarting, or getting the service status

#### start mypackage

```bash
sudo systemctl start mypackage
```

#### stop mypackage

```bash
sudo systemctl stop mypackage
```

#### restart mypackage

```bash
sudo systemctl restart mypackage
```

#### get mypackage service status

```bash
sudo systemctl status mypackage
```

## Adding new packages to the existing repository

```bash
EMAIL=<private-key-email>
GITHUB_USERNAME=<your-github-username>
REPO_NAME=<your-github-reponame>
# add new .deb package in to the root folder of the repo
gpg --import my-private-key.asc
dpkg-scanpackages --multiversion . > Packages
gzip -k -f Packages
apt-ftparchive release . > Release
gpg --default-key "${EMAIL}" -abs -o - Release > Release.gpg
gpg --default-key "${EMAIL}" --clearsign -o - Release > InRelease
```

### Commit and push to GitHub and your PPA is ready to go:

```bash
git add -A
git commit -m "addded a new package to the repo"
git push -u origin master
```
### install your PPA this way

```bash
curl -s --compressed "https://${GITHUB_USERNAME}.github.io/my_ppa/KEY.gpg" | sudo apt-key add -
sudo curl -s --compressed -o /etc/apt/sources.list.d/my_list_file.list "https://${GITHUB_USERNAME}.github.io/my_ppa/my_list_file.list"
sudo apt update
```

### install your packages:

```bash
sudo apt install package-a package-b package-z
```

### Help

>- <https://assafmo.github.io/2019/05/02/ppa-repo-hosted-on-github.html>

