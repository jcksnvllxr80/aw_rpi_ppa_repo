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

>- <https://assafmo.github.io/2019/05/02/ppa-repo-hosted-on-github.html>
