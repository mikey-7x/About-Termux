# 📱🪲🐊📟🍁🌿🌾 About Termux – Complete Guide for Beginners & Power Users

> This repository is a complete, beginner-friendly guide to using **Termux** on Android. Learn how to set it up, install powerful tools, and use Linux like a pro – all from your phone, with or without root access.

---

## 📚 Table of Contents

1. [🍁 What is Termux?](#-what-is-termux)
   
2. [🔧 Initial Setup](#-initial-setup)
   
3. [🛠️ Essential Tools](#-essential-tools)
   
4. [📂 Storage Access](#-storage-access)
   
5. [💻 Linux in Termux (Proot-Distro)](#-linux-in-termux-proot-distro)
    
6. [🧰 Toolkits & Use Cases](#-toolkits--use-cases)

7. [🪲 About Termux](#-about-termux)
    
8. [⚠️ Troubleshooting & Tips](#-troubleshooting--tips)
    
9. [🧠 Contribute](#-contribute)

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

## 🛠️ Essential Tools

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

## 🪲 About Termux

**(1)All Major Usable Scripting Languages in Termux (Android)**

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


## 🧠 Contribute

Have useful commands or scripts?
PRs and issues are welcome!


---

📢 Stay Updated

🔗 Termux Wiki

🔗 r/termux subreddit

🔗 Awesome-Termux List



---

> Made with 💻❤️ by @mikey-7x – Keep hacking, keep learning!



---



