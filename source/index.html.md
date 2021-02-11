---
title: ComputeDocs

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://github.com/samarthdave/slate'>Contribute</a>

search: true
---

# Welcome

Hey! As students at A&M, we're given access to the central "Compute" service (hosted at compute.cs.tamu.edu). This site will help you set up a connection and your environment.

# Overarching Steps
1. **Connect to TAMU VPN** ([connect.tamu.edu](https://connect.tamu.edu)) if you're not connected to campus wifi.
  - **Skip this step if you're on campus (connected to TAMU wifi)**
  - *MacOS & Linux*: Download Cisco AnyConnect or openconnect
  - *Windows*: Download Cisco Anyconnect
2. **SSH into compute** through some terminal program
  - *MacOS & Linux*: native Terminal Program or [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
  - *Windows*: [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) or PowerShell (yuck)
3. Set up a workflow (my set up is below).
4. Get coding ;)

# Windows Users

## 1) Install VPN Client (Cisco Anyconnect recommended)
1. Go to [https://connect.tamu.edu](https://connect.tamu.edu).
2. Log in with NetID & password.
3. Install the "Cisco AnyConnect Secure Mobility Client" for Windows.
  - **Alternatively**, install AnyConnect from [Cisco's website](https://www.cisco.com/c/en/us/support/security/anyconnect-secure-mobility-client-v4-x/model.html#~tab-downloads).

## 1.5) Connecting to TAMU VPN - only for off-campus users
2. Open Cisco Anyconnect.
3. In the prompt, type in `connect.tamu.edu` and press **Connect**.
4. Type in username (NetID) and password.
5. Approve sign in with [Duo Authentication](https://apps.apple.com/us/app/duo-mobile/id422663827).

## 2) SSH into Compute

```bash
=================================================
                PuTTY Configuration
=================================================
Host Name (or IP address) --> compute.cs.tamu.edu
Port                      --> 22
Connection Type           --> SSH (default)
Saved Sessions            --> Any name to save yourself time
```

1. Open PuTTY
2. Use the configuration on the right to connect.
3. Press **Open** to test connection with TAMU Compute Servers.
  - Tip: To save yourself time, type something into *Saved Sessions* and press **Save**
4. An alert box will pop up for first time connections. **Press "Yes"** to trust the Compute servers.
5. Type in your username / NetID
6. Type in your password.
7. Done deal.

# MacOS Users

## 1) Install VPN Client (Cisco Anyconnect recommended)
1. Go to [https://connect.tamu.edu](https://connect.tamu.edu).
2. Log in with NetID & password.
3. Install the "Cisco AnyConnect Secure Mobility Client" for MacOS.
  - **Alternatively**, install AnyConnect from [Cisco's website](https://www.cisco.com/c/en/us/support/security/anyconnect-secure-mobility-client-v4-x/model.html#~tab-downloads).

## 1.5) Connecting to TAMU VPN
1. **Skip this step if you're on campus (connected to TAMU wifi)**
2. Open Cisco Anyconnect.
3. In the prompt, type in `connect.tamu.edu` and press **Connect**.
4. Type in username (NetID) and password.
5. Approve sign in with [Duo Authentication](https://apps.apple.com/us/app/duo-mobile/id422663827).

## 2) SSH into Compute
1. Open up your terminal app
```
Command + Space > "Terminal"
```

2. Enter the command ```ssh``` and you should get the output you see on the right.

```bash
MacOS_user $ ssh # run "ssh" in the terminal
usage: ssh [-46AaCfGgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-E log_file] [-e escape_char]
           [-F configfile] [-I pkcs11] [-i identity_file]
           [-J [user@]host[:port]] [-L address] [-l login_name] [-m mac_spec]
           [-O ctl_cmd] [-o option] [-p port] [-Q query_option] [-R address]
           [-S ctl_path] [-W host:port] [-w local_tun[:remote_tun]]
           [user@]hostname [command]
```

3. Copy the command below. Be sure to replace the *MY_USERNAME* with the handle that you use to login to A&M services. **Note, this is not your UIN.**

```bash
$ ssh MY_USERNAME@compute.cs.tamu.edu
# "compute.cse.tamu.edu" does the same
```

```
The authenticity of host 'blah.blah.blah (10.10.10.10)' can't be established.
RSA key fingerprint is a4:d9:a4:d9:a4:d9a4:d9:a4:d9a4:d9a4:d9a4:d9a4:d9a4:d9.
Are you sure you want to continue connecting (yes/no)?
```

# Development Setup

## Windows

Install the following:

- [VS Code](https://code.visualstudio.com/Download)
- [VS Code Extension - SSH File System](https://marketplace.visualstudio.com/items?itemName=Kelvin.vscode-sshfs)
- Cisco Anyconnect (link above)
- Putty (or powershell)

## MacOS

Install the following:
- [VS Code](https://code.visualstudio.com/Download)
- [VS Code Extension - SSH File System](https://marketplace.visualstudio.com/items?itemName=Kelvin.vscode-sshfs)
- Cisco Anyconnect (link above)
  - **or** [install "openconnect"](https://people.eng.unimelb.edu.au/lucasjb/archive/oc_old.html) for terminal (macOS or Linux flavors)

# Setting up SSH FS

1. Either use on-campus wifi or connect to the vpn.

Cisco Openconnect in the terminal:

```bash
$ sudo openconnect connect.tamu.edu

enter username, password, duo authentication, etc.
...
POST https://connect.tamu.edu/
Got CONNECT response: HTTP/1.1 200 OK
```

2. `Ctrl+Shift+P` in VSCode > ">SSH FS: Create a SSH FS configuration"
3. Name it and press save.
4. Now fill out the following fields on the right:

```bash
Hostname:
compute.cs.tamu.edu
--------------------------------------
Root - uses your username and the first letter of it:
/home/ugrads/w/wanda
/home/ugrads/v/vision
/home/ugrads/n/netID, etc.
--------------------------------------
Username - your netID:
wanda
--------------------------------------
Password: either prompt or save it
--------------------------------------
```

5. Press save
6. Click the icon on the left for the extension & press the "folder +" sign to add to workspace
7. It will prompt for your password and then connect.
