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
sudo apt install berrycam
```

### Updating the berrycam service

```bash
apt install --only-upgrade berrycam
```

### Uninstall the service

```bash
sudo apt remove berrycam -y
```

### Starting, stopping, restarting, or getting the service status

#### start berryCam

```bash
sudo systemctl start berryCam
```

#### stop berryCam

```bash
sudo systemctl stop berryCam
```

#### restart berryCam

```bash
sudo systemctl restart berryCam
```

#### get berryCam service status

```bash
sudo systemctl status berryCam
```
