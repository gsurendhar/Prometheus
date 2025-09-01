# Prometheus Installation Guide

This guide provides step-by-step instructions to install Prometheus  on a Linux system.

## Prerequisites

- A running Linux instance (e.g:- RHEL, Ubuntu, CentOS).
- Root/sudo access to the instance.
- `wget`, `tar`, and `vim` must be installed.

## Steps

### 1. Switch to the root user

```
sudo su -
```

### 2. Navigate to the /opt directory

```
cd /opt/
```

### 3. Download Prometheus

```
wget https://github.com/prometheus/prometheus/releases/download/v3.6.0-rc.0/prometheus-3.6.0-rc.0.linux-amd64.tar.gz
```

### 4. Extract the archive

```
tar -xf prometheus-3.6.0-rc.0.linux-amd64.tar.gz
```
### 5. Rename the extracted folder

```
mv prometheus-3.6.0-rc.0.linux-amd64.tar.gz prometheus
```

### 6. Create a systemd service file for Prometheus

```
vim /etc/systemd/system/prometheus.service
```

* Add the following content to the file:

```
[Unit]
Description=Prometheus Monitoring
After=network.target

[Service]
Restart=on-failure
ExecStart=/opt/prometheus/prometheus  --config.file=/opt/prometheus/prometheus.yml 

[Install]
WantedBy=multi-user.target
```

### 7. Reload systemd and restart Prometheus

```
systemctl daemon-reload
```
```
systemctl restart prometheus
```

### 8. Verify Prometheus is running

```
netstat -lntp
```
Look for Prometheus listening on port 9090.

* Access Prometheus

Open your browser and navigate to:
http://your-server-public-ip:9090




# Grafana Installation Guide

This guide provides step-by-step instructions to install Grafana  on a Linux system.


## Steps

### 1. Switch to the root user

```
sudo su -
```

### 2. Import the GPG key:
```
wget -q -O gpg.key https://rpm.grafana.com/gpg.key
```
```
sudo rpm --import gpg.key
```

### 3. Create `/etc/yum.repos.d/grafana.repo` with the following content:
```
vim /etc/yum.repos.d/grafana.repo
```
```
[grafana]
name=grafana
baseurl=https://rpm.grafana.com
repo_gpgcheck=1
enabled=1
gpgcheck=1
gpgkey=https://rpm.grafana.com/gpg.key
sslverify=1
sslcacert=/etc/pki/tls/certs/ca-bundle.crt
```

### 4. To install Grafana OSS, run the following command:

```
sudo dnf install grafana -y
```

### 5. Reload systemd and restart Grafana

```
systemctl daemon-reload
```
```
systemctl start grafana-server
```

### 6. Enable Grafana systemd service

```
systemctl enable grafana-server
```

### 7. Verify Grafana is running

```
netstat -lntp
```
Look for Grafana listening on port 3000.

* Access Grafana

Open your browser and navigate to:
"http://<your-server-public-ip>:3000"

### 8. Login to Grafana 
* By using username : `admin` and password : `admin`

