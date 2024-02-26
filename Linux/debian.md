# Install Neovim

```bash
curl -Lo neovim.tar.gz https://github.com/neovim/neovim/releases/latest/download/nvim-linux64.tar.gz
sudo tar xzvf neovim.tar.gz -C /opt/
sudo ln -s /opt/nvim-linux64/bin/nvim /usr/local/bin/nvim
source ~/.bashrc
```

# Install LazyGit

```bash
LAZYGIT_VERSION=$(curl -s "https://api.github.com/repos/jesseduffield/lazygit/releases/latest" | grep -Po '"tag_name": "v\K[^"]*')
curl -Lo lazygit.tar.gz "https://github.com/jesseduffield/lazygit/releases/latest/download/lazygit_${LAZYGIT_VERSION}_Linux_x86_64.tar.gz"
tar xf lazygit.tar.gz lazygit
sudo install lazygit /usr/local/bin
```

# Install Edge

```bash
sudo apt install software-properties-common apt-transport-https ca-certificates curl -y
curl -fSsL https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor | sudo tee /usr/share/keyrings/microsoft-edge.gpg > /dev/null
echo 'deb [signed-by=/usr/share/keyrings/microsoft-edge.gpg] https://packages.microsoft.com/repos/edge stable main' | sudo tee /etc/apt/sources.list.d/microsoft-edge.list
sudo apt update && sudo apt install microsoft-edge-stable
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
