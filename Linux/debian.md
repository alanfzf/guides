# Install Neovim

```bash
curl -L "https://github.com/neovim/neovim/releases/latest/download/nvim-linux64.tar.gz" | sudo tar xzf - -C /opt/
sudo ln -sf /opt/nvim-linux64/bin/nvim /usr/local/bin/nvim
```

# Install LazyGit

```bash
LAZYGIT_VERSION=$(curl -s "https://api.github.com/repos/jesseduffield/lazygit/releases/latest" | grep -Po '"tag_name": "v\K[^"]*')
curl -L "https://github.com/jesseduffield/lazygit/releases/latest/download/lazygit_${LAZYGIT_VERSION}_Linux_x86_64.tar.gz" | sudo tar xzf - -C /usr/local/bin/
```

# Install eza

```bash
sudo mkdir -p /etc/apt/keyrings
wget -qO- https://raw.githubusercontent.com/eza-community/eza/main/deb.asc | sudo gpg --dearmor -o /etc/apt/keyrings/gierens.gpg
echo "deb [signed-by=/etc/apt/keyrings/gierens.gpg] http://deb.gierens.de stable main" | sudo tee /etc/apt/sources.list.d/gierens.list
sudo chmod 644 /etc/apt/keyrings/gierens.gpg /etc/apt/sources.list.d/gierens.list
sudo apt update && sudo apt install -y eza
```

# Change default audio output

```bash
# list all available outputs
pactl list short sinks
# set the output
pactl set-default-sink [number]
```
# Manage Bluetooth

```bash
comandos para bluetooth
bluetoothctl
power on
scan on 
pair XX:XX:XX
trust XX:XX:XX
connect XX:XX:XX
agent on
```
