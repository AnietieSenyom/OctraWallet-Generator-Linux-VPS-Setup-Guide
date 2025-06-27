# 🔐 Octra Wallet Generator — Linux VPS Setup Guide

A secure and efficient way to generate Octra wallets directly from your own VPS.  
This guide walks you through setting up and running the **Octra Wallet Generator v4** using the **pre-built Linux binary**, with persistent background sessions using `screen`.

---

## 📦 Dependencies

Ensure the following tools are installed on your VPS:

- `wget` – for downloading files  
- `tar` – for extracting `.tar.gz` archives  
- `screen` – to keep the generator running in the background

Install them with:

```bash
sudo apt update
sudo apt install -y wget tar screen
```

---

## 🖥️ Start a Persistent Screen Session

Start a `screen` session to keep the wallet generator alive even after disconnection:

```bash
screen -S octa
```

You’ll be dropped into a new terminal window inside the screen session.

> To detach: `Ctrl + A`, then `D`  
> To reattach:  
```bash
screen -r octa
```  
> To exit and stop: type `exit` inside the screen

---

## 📥 Download and Run the Pre-Built Wallet Generator

**Step 1: Download the Pre-Built Binary**

```bash
wget https://github.com/octra-labs/wallet-gen/releases/download/v4/wallet-generator-linux-x64.tar.gz
```

**Step 2: Extract the Archive**

```bash
tar -xzf wallet-generator-linux-x64.tar.gz
```

**Step 3: Make the Binary Executable**

```bash
chmod +x wallet-generator
```

**Step 4: Run the Wallet Generator**

```bash
./wallet-generator
```

---

## 🌐 Open the Web Interface

Access the interface from your local browser:

```
http://<your-vps-ip>:8888
```

> Example:  
If your VPS IP is `192.168.1.100`, visit:  
```
http://192.168.1.100:8888
```

You’ll see the Octra Wallet Generator interface — click **"Generate New Wallet"** to begin.

---

## 🔓 Open Firewall Port 8888 (If Needed)

If the web interface doesn't load, open the port:

**For UFW users:**

```bash
sudo ufw allow 8888/tcp
sudo ufw reload
```

**For iptables users:**

```bash
sudo iptables -A INPUT -p tcp --dport 8888 -j ACCEPT
```

---

## ⚠️ Security Notes

- **Never share your mnemonic or private keys**
- **Do not store wallets on cloud storage**
- **For real wallets, use this tool only on secure or air-gapped machines**
- **Back up generated keys immediately and securely**

---

## 🧵 Screen Commands Summary

- Start session:  
```bash
screen -S octa
```

- Detach session:  
`Ctrl + A`, then `D`

- Reattach session:  
```bash
screen -r octa
```

- Exit session:  
Type `exit` inside the screen window

---

## ✅ Done!

You now have the Octra Wallet Generator running securely and persistently on your VPS.
