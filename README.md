# Talaria.sh
A minimal minecraft server management cli-app using Bash. Intended for Linux systems.


## Table of Contents
- [About](#about)
- [Dependencies](#dependencies)
- [Pre-installation](#pre-installation)
- [Installation](#installation)
- [Usage](#usage)


## About
[`talaria`](https://github.com/wasique-sh/talaria.sh/blob/master/talaria) simplifies managing one minecraft server per linux system. In addition, it does the following:
- Start and Stop the server in a safe and reliably manner
- Automatically restart the server whenever it crashes
- Keeps the server running even if the terminal is closed
- View the server status at a glance
- Interact with the server console


## Dependencies
- [Screen](https://www.gnu.org/software/screen/)
- [OpenJDK 17](https://openjdk.org/projects/jdk/17/)


## Pre-installation
1. Login into Linux as **non-root** user
2. Make sure **git**, **screen** and **openjdk 17** is installed
3. Create a `minecraft` folder inside the `home` folder by running the following commands
```sh
mkdir -p ~/minecraft
```
4. Download **Minecraft Server** jar file from [Minecraft](https://www.minecraft.net/en-us/download/server) or [Paper](https://papermc.io/downloads/paper), rename it to `server.jar` and place it inside the `minecraft` folder
5. Run the `server.jar` file (inside the `minecraft` folder) using the following command
```sh
cd ~/minecraft
java -Xmx2G -Xms1G -jar "server.jar" nogui
```
6. Accept the **Minecraft EULA** in `eula.txt` (inside the `minecraft` folder) using a text editor or by running the following command
```sh
sed -i "s/false/true/g" ~/minecraft/eula.txt
```
7. (Optional) Set the Server Settings in `server.properties` (inside the `minecraft` folder as well) using a text editor
8. Make sure `25565 TCP/UDP` port is open in System **Firewall**
9. (Optional) Enable Port forward (in router) and have public static IP or use services like [ngrok](https://ngrok.com/) to play with friends outside LAN


## Installation
```sh
git clone https://github.com/wasique-sh/talaria.sh.git
cd talaria.sh
chmod +x talaria
sed -i "s/USERNAME/$USER/g" talaria

mkdir -p ~/.local/bin
mv talaria ~/.local/bin

# Add local/bin to PATH
if [[ ":$PATH:" != *":$HOME/.local/bin:"* ]]; then
    echo 'export PATH="$PATH:$HOME/.local/bin"' >> ~/.bashrc
fi
```
(Optional) Edit `~/.local/bin/talaria` file to change RAM values and Directory locations


## Usage
**Start Server**
```sh
talaria start
```

**Stop Server**
```sh
talaria stop
```

**Force Stop Server**
```sh
talaria kill
```
- Use only when server freezes

**View Server Console and interact with it**
```sh
talaria view
```
- Exit Console View by 
    - pressing `CTRL+a` and then `d`
    - Or, closing the terminal

**Check Server Status**
```sh
talaria ping
```

**Print Talaria Version**
```sh
talaria version
```
