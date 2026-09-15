# 🛡️ Mojo Vault

Mojo Vault is an educational browser-based geolocation demonstration for students and cybersecurity learners. It shows how a web page can request a device's approximate location — latitude, longitude, accuracy, and IP — only after the user explicitly grants permission through the browser's built-in geolocation API.

The project is meant to teach how consent-based location sharing works and how a front end (JavaScript) passes data to a back end (PHP) for logging. It is not a spying or hacking tool, and it should only be used in controlled, consent-based environments that you own or have explicit permission to test.

## 🎯 Purpose

- Demonstrate how browser geolocation permission requests work.
- Show how front-end JavaScript sends captured data to a back-end script.
- Illustrate how location data can be logged for study, with consent and local hosting.

## 💻 Platform support

- **Termux (Android)** — Fully supported. Includes optional Termux helpers (`termux-clipboard-set`, `termux-toast`).
- **Linux (Debian / Ubuntu / Kali)** — Fully supported. Recommended for desktop or VM use.
- **macOS / Windows** — May work via WSL or XAMPP, but is not officially supported.

## ⚙️ Installation

```bash
apt update && apt upgrade

git clone https://github.com/mojoolabs/Mojo-Vault.git
cd Mojo-Vault

bash mojovault.sh
```

The script installs the required packages (php, ssh, wget, and optional tunneling tools), starts a local PHP server on `127.0.0.1:8080`, and lets you choose a tunnel option (localhost, Cloudflared, or Serveo).

## 🔍 How it works

1. The page requests location permission. If the user allows, `navigator.geolocation.getCurrentPosition` captures the coordinates client-side.
2. The front end POSTs the coordinates to `save_location.php` on the same host.
3. `save_location.php` appends the data to `locations.txt`, and the script prints new entries as they arrive.

## 📁 Files

- `index.html` — Front-end page and geolocation logic.
- `save_location.php` — Receives POSTed coordinates and logs them.
- `mojovault.sh` — Setup script: installs dependencies, starts the server, and monitors logs.
- `locations.txt` — Logged location entries.
