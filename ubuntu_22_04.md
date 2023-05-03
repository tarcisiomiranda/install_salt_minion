# Install salt 3005.x on Ubuntu 20.04

***add new repo***
```
sudo curl -fsSL -o /etc/apt/keyrings/salt-keyring.gpg https://repo.saltproject.io/salt/py3/ubuntu/22.04/amd64/3005/salt-archive-keyring.gpg && \
echo "deb [signed-by=/etc/apt/keyrings/salt-keyring.gpg arch=amd64] https://repo.saltproject.io/salt/py3/ubuntu/22.04/amd64/3005 jammy main" | sudo tee /etc/apt/sources.list.d/salt.list
```

***removing old versions***
```
apt remove salt salt-common salt-master salt-minion
apt update
```

***remove misc files and add minion id***
```
rm /etc/salt/minion && echo $(hostname) > /etc/salt/minion_id
```

***file for salt-master***
```
echo "master: YOUR_MASTER" > /etc/salt/minion.d/master.conf
```

***restart service***
```
systemctl restart salt-minion
```
