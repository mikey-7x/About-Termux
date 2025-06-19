# 📱 About Termux – Complete Guide for Beginners & Power Users

> This repository is a complete, beginner-friendly guide to using **Termux** on Android. Learn how to set it up, install powerful tools, and use Linux like a pro – all from your phone, with or without root access.

---

## 📚 Table of Contents

1. [📦 What is Termux?](#-what-is-termux)
2. [🔧 Initial Setup](#-initial-setup)
3. [🛠️ Essential Tools](#️-essential-tools)
4. [📂 Storage Access](#-storage-access)
5. [💻 Linux in Termux (Proot-Distro)](#-linux-in-termux-proot-distro)
6. [🧰 Toolkits & Use Cases](#-toolkits--use-cases)
7. [⚠️ Troubleshooting & Tips](#️-troubleshooting--tips)
8. [🧠 Contribute](#-contribute)

---

## 📦 What is Termux?

**Termux** is an Android terminal emulator and Linux environment app that doesn’t require rooting. You can:

- Run Linux packages and shells
- Install programming environments (Python, Node, etc.)
- Run SSH servers, Git, Kali, Ubuntu, and more!

🔗 [Official Termux F-Droid Page](https://f-droid.org/packages/com.termux/)

---

## 🔧 Initial Setup

1. ✅ **Install Termux from F-Droid** *(Do NOT use Play Store version)*

➤ [https://f-droid.org/packages/com.termux/](https://f-droid.org/packages/com.termux/)

2. ✅ **Update and Upgrade Packages**
```bash
pkg update && pkg upgrade -y
```

3. ✅ Install Basic Essentials
```
pkg install python git curl wget nano openssh -y
```

4. ✅ Fix Mirrors (if slow)
```
termux-change-repo
```

---

🛠️ Essential Tools
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

application-based tools

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

📂 Storage Access

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

💻 Linux in Termux (Proot-Distro)

Want full Linux inside Termux? Use proot-distro.

✅ Install Ubuntu / Kali / Fedora:
```
proot-distro install ubuntu
proot-distro login ubuntu
```

Now you’re inside Ubuntu. You can install tools with apt, set up xfce, mitmproxy, dirsearch, and more.


---

🧰 Toolkits & Use Cases

🔎 Dirsearch (Web Directory Brute Force)
```
git clone https://github.com/maurosoria/dirsearch.git
cd dirsearch
pip install -r requirements.txt
python3 dirsearch.py -u https://example.com -e php,html
```

---

🔍 mitmproxy (HTTP/HTTPS Sniffer)
```
pip install mitmproxy
mitmproxy --listen-port 8080
```

Use to inspect mobile traffic. For advanced use, install cert on second device, set proxy, and run HTTP server.


---

🐍 AndroRAT (Educational RAT)
```
git clone https://github.com/karma9874/AndroRAT.git
cd AndroRAT
python3 -m venv env
source env/bin/activate
pip install -r requirements.txt
python3 androRAT.py --build -i <your_ip> -p 8000 -o rat.apk
```

⚠️ For educational use only. Never use without consent.


---

⚠️ Troubleshooting & Tips

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

🧠 Contribute

Have useful commands or scripts?
PRs and issues are welcome!


---

📢 Stay Updated

🔗 Termux Wiki

🔗 r/termux subreddit

🔗 Awesome-Termux List



---

> Made with 💻♥️ by @mikey-7x – Keep hacking, keep learning!



---



