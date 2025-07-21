# 🛠️ Airgeddon WiFi Cracking Lab Setup - README

## ⚠️ Disclaimer
This setup is strictly for **educational purposes** and should be done in a **controlled lab environment** with **your own network** or with **explicit permission**. Unauthorized access to WiFi networks is illegal and unethical.

---

## 🧪 Objective

Set up and configure the **Airgeddon** tool in a controlled lab environment to simulate a WiFi password cracking scenario. This involves:

- Setting up the environment
- Installing required dependencies
- Using Airgeddon to scan and attack WiFi
- Capturing the WPA handshake
- Cracking the handshake with a wordlist

---

## ✅ Prerequisites

- A system with **Kali Linux** or **Parrot OS**
- A wireless network adapter with **monitor mode** and **packet injection** support (e.g., ALFA AWUS036NHA)
- Root/sudo access

---

## 🧰 Step-by-Step Setup & Commands

### 1. 🔧 Install Dependencies

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install git aircrack-ng isc-dhcp-server hashcat bully pixiewps -y
```

### 2. 📥 Clone Airgeddon

```bash
git clone https://github.com/v1s1t0r1sh3r3/airgeddon.git
cd airgeddon
```

📸 **Screenshot to capture**: Terminal after cloning Airgeddon repo.

---

### 3. 🔍 Detect Wireless Interfaces

```bash
iwconfig
```

- Identify your wireless interface (e.g., `wlan0`)

📸 **Screenshot to capture**: Output showing interface names.

---

### 4. 📡 Enable Monitor Mode

```bash
sudo airmon-ng start wlan0
```

- This creates a new interface like `wlan0mon`

📸 **Screenshot to capture**: Interface put into monitor mode.

---

### 5. 🚀 Launch Airgeddon

```bash
sudo bash airgeddon.sh
```

📸 **Screenshot to capture**: Airgeddon main menu.

---

## 🕵️‍♂️ WiFi Cracking Process Using Airgeddon

### 6. 📶 Select Wireless Adapter

- Choose `wlan0mon` or your monitor-mode interface from the list.

📸 **Screenshot**: Interface selection screen.

---

### 7. 🔍 Select Attack Type

- Choose: **Handshake Capture Attack**

📸 **Screenshot**: Attack selection menu.

---

### 8. 🧠 Select Target Network

- Airgeddon will open a scanning window.
- Press `Ctrl+C` when you see your **test WiFi network**.
- Select it from the list.

📸 **Screenshot**: Target AP selection screen.

---

### 9. 📡 Deauthentication

- Select **deauth attack** to disconnect clients.
- Airgeddon will capture the WPA handshake when clients reconnect.

📸 **Screenshot**: Deauth and handshake capture progress.

---

### 10. 📁 Verify Handshake

- Airgeddon will automatically verify the captured handshake.

📸 **Screenshot**: Successful handshake verification.

---

### 11. 🔐 Crack the Password

- Choose **offline cracking using wordlist**
- Select your **wordlist** (e.g., `rockyou.txt`)

```bash
sudo gunzip /usr/share/wordlists/rockyou.txt.gz
```

📸 **Screenshot**: Cracking in progress and result (if password is found).

---

## 📂 Output Files

Airgeddon stores capture files in the `/root/handshakes` or the directory you set. The key files include:

- `.cap` (capture file)
- `.hccapx` (for Hashcat)
- `.txt` (cracked password, if successful)

---

## 📌 Notes

- Best results occur when the victim device is actively connected.
- Ensure your adapter supports **packet injection**.
- If no handshake is captured, retry deauth or use a better antenna.

---

## 📷 Screenshots Summary

| Step | Screenshot Description |
|------|------------------------|
| 1 | Cloned Airgeddon repository |
| 2 | Detected interfaces via `iwconfig` |
| 3 | Monitor mode activated via `airmon-ng` |
| 4 | Airgeddon main menu |
| 5 | Interface selection |
| 6 | Handshake attack selection |
| 7 | Target network selected |
| 8 | Deauthentication and capture process |
| 9 | Handshake verification |
| 10 | Wordlist cracking in progress |
| 11 | Cracked password (if successful) |

---

