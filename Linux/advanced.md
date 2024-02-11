# Network commands

## Connect to WiFi network

```bash
nmcli device wifi list
nmcli device wifi connect SSID_NAME password PASSWORD
```

## Set a static IP

```bash
cd /etc/netplan/
sudo vi 00-installer-config.yaml
# apply changes 
sudo netplan apply
```

```yml
# change to this
network:
  renderer: networkd
  ethernets:
    ens33:
      addresses:
        - 192.168.1.247/24
      nameservers:
        addresses: [4.2.2.2, 8.8.8.8]
      routes:
        - to: default
          via: 192.168.1.1
  version: 2
```

# Generation commands

## Generate a private and public SSH key

```bash
ssh-keygen -t rsa -b 4096 -C "example@email.com"
```

```bash
ssh-keygen -t rsa-sha2-256 -b 2048
```

## Generate a random base64 string

```bash
cat /dev/urandom | head -c 64 | base64
```

# Misc commands

```bash
# Get free space
df -h
# Get RAM info
free -h
```
