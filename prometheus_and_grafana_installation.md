* Launch the instance

 ```
sudo su -
```

```
cd /opt/
```

```
wget https://github.com/prometheus/prometheus/releases/download/v3.6.0-rc.0/prometheus-3.6.0-rc.0.linux-amd64.tar.gz
```

```
tar -xf prometheus-3.6.0-rc.0.linux-amd64.tar.gz
```

```
mv prometheus-3.6.0-rc.0.linux-amd64.tar.gz prometheus
```

```
vim /etc/systemd/system/prometheus.service
```

```
systemctl daemon-reload
```

```
systemctl restart prometheus
```

```
netstat -lntp
```