# Windows Subsystem for Linux

```bash
# enable close, minimize and resize WSL
gsettings set org.gnome.desktop.wm.preferences button-layout ":minimize,maximize,close"
```

```bash
# open ports on host machine
# https://www.nextofwindows.com/allow-server-running-inside-wsl-to-be-accessible-outside-windows-10-host
netsh interface portproxy reset
netsh interface portproxy add v4tov4 listenport=3000 listenaddress=0.0.0.0 connectport=80 connectaddress=172.31.178.209
netsh interface portproxy add v4tov4 listenport=3306 listenaddress=0.0.0.0 connectport=3306 connectaddress=172.31.178.209
netsh interface portproxy add v4tov4 listenport=22 listenaddress=0.0.0.0 connectport=22 connectaddress=172.31.178.209
```
