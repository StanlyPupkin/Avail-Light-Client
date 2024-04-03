# Avail-Light-Client
#Avail-Light-Client

#This instructions start after you succesfully connetced to your server 

***
Upgrade Your machine
**sudo apt-get update && sudo apt upgrade**

1)**Go to directory**

```
 сd root
```

2)**Create directory**

```
cd $HOME
mkdir -p avail-light-client
cd avail-light-client
```

3)**Download the latest stable version compatible with your system: https://github.com/availproject/avail-light/releases/tag/v1.7.9**

**(If You running simple on VPS unbuntu just copy past below example)**

**Example:**

```
wget https://github.com/availproject/avail-light/releases/download/v1.7.9/avail-light-linux-amd64.tar.gz
```

4)**Extract it:**

```
tar -xvzf avail-light-linux-amd64.tar.gz
cp avail-light-linux-amd64 avail-light
rm -r avail-light-linux-amd64.tar.gz
```

5)**Go to directory**

```
 cd /avail-light/target/release
```

6)**Create identity.toml file:**

```
touch identity.toml
nano identity.toml
```

7)**Paste this and enter your avail wallet seed:**

```
avail_secret_seed_phrase = 'enter_your_seed_here'
```

**Dont miss to use ' both sides of your seed**
**Example:**
```
avail_secret_seed_phrase = 'toe vinegar face chain ...'

```

8)**Create Systemd file:**

```
touch /etc/systemd/system/availdlight.service
nano /etc/systemd/system/availdlight.service
```

9)**Paste this content:**

```
[Unit]
Description=Avail Light Client
After=network.target
StartLimitIntervalSec=0
[Service]
User=root
ExecStart=/root/avail-light-client/avail-light-linux-amd64 --network goldberg --identity /root/avail-light-client/identity.toml
Restart=always
RestartSec=120
[Install]
WantedBy=multi-user.target
```

**Save it: ctrl x + y + enter**

10)**Starting service:**

```
sudo systemctl daemon-reload
sudo systemctl enable availdlight.service
sudo systemctl start availdlight.service
```

11)**Checking if node running:**

```
systemctl status availdlight.service
```

**Example:**

<img width="900" alt="image" src="https://github.com/StanlyPupkin/Avail-Light-Client/assets/162813598/dbdefada-39bf-49fe-96d6-fa8305c33483">

12)**Checking logs:**

```
journalctl -u availdlight -fo cat
```

**Example:**

<img width="900" alt="image" src="https://github.com/StanlyPupkin/Avail-Light-Client/assets/162813598/0e52b392-29ce-4d4f-870c-6d87f387a387">

















