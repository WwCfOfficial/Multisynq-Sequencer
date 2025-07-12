# 🌀 multisynq-sequencer Node Setup Guide (VPS Edition)

This guide walks you through setting up the [`synchronizer-cli`] node on your **Linux VPS** using Docker. It covers installation, configuration, systemd service setup, and basic operations.

* Docs: [synchronizer-cli](https://github.com/multisynq/synchronizer-cli)
* Twitter/X: [@multisynq](https://x.com/multisynq)
* Discord: [Multisynq_Discord](https://discord.gg/xjAahkDpz7)

---

# Join WwCf Airdrop Community

Join TG : [WwCf Airdrop Telegram](https://t.me/WwCfAirdrops) 

Follow X : [WwCf Airdrop Twitter](https://x.com/WwCfOfficial) 

Subscribe : [WwCf Airdrop Youtube](https://youtube.com/@WwCfOfficial)


# VPS Options

💻 Contabo VPS Deals or Servarica VPS it's good  🚀 Buy with Credit Card/Paypal/Crypto Credit card : 



---

## ⚙️ Requirements

- ✅ Linux VPS
- ✅ Node.js v10+ and npm
- ✅ Synq Key from [Multisynq Dashboard](https://startsynqing.com/?ref=048aca-x7tksn)
- ✅ Docker installed (auto setup supported)

---

## Install dependencies
```
sudo apt update && sudo apt upgrade -y
sudo apt install -y curl
```

## Install Nodejs

```
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt install -y nodejs
node -v
npm -v
```


## 📦 Install synchronizer-cli

```bash
sudo npm install -g synchronizer-cli
````

> This installs the latest global version of `synchronizer-cli` on your system.

---

## 🐳 Setup Docker (if not already installed)

```bash
synchronize install-docker
synchronize fix-docker
```

> ✅ Adds Docker, sets permissions, and verifies install.

---

## 🔐 Initialize the Node (Interactive)

```bash
synchronize init
```

This prompts you to enter:

* Your **Synq Key**
* Your **Wallet Address**
* Port, Name, and Password for your node

---

## 🚀 Quick One-Liner Deployment

You can skip the `init` prompt and use:

```bash
synchronize deploy -k YOUR_SYNQ_KEY -w 0xYourWalletAddress -n "MyVPSNode" -p 3000 -m 3001 --password "YourSecurePassword"
```

---
-k — your Synq Key

-w — your wallet address

-n — node name

-p — node port (e.g., 3000)

-m — metrics port (e.g., 3001)

--password — node password

---

> This will auto-generate config and launch the Docker-based node immediately.

---

## 🧩 Setup as a systemd Service

To run automatically on boot:

```bash
synchronize service
synchronize service-web
```

Move the services to system folder:

```bash
sudo cp ~/.synchronizer-cli/*.service /etc/systemd/system/
```

Reload & enable:

```bash
sudo systemctl daemon-reload
sudo systemctl enable synchronizer-cli synchronizer-cli-web
sudo systemctl start synchronizer-cli synchronizer-cli-web
```

Also allow dashboard ports if not already allowed

```bash
sudo ufw allow 3000/tcp
sudo ufw allow 3001/tcp
```

Check UFW status and allowed ports:

```bash
sudo ufw status
```

---

## 📊 Monitor via Web Dashboard

Visit:

```
http://<your-vps-ip>:3000
```

Or if you set a custom port, use it. The metrics server is available at `PORT + 1`.

---

## 🛠️ Useful Commands

| Command                             | Description                               |
| ----------------------------------- | ----------------------------------------- |
| `synchronize start`                 | Start node manually                       |
| `synchronize web`                   | Start dashboard server                    |
| `synchronize points`                | View your lifetime points                 |
| `synchronize status`                | See node status                           |
| `synchronize set-password`          | Reset dashboard login password            |
| `synchronize validate-key YOUR_KEY` | Verify if Synq Key is valid               |
| `synchronize test-platform`         | Check platform compatibility (ARM vs AMD) |

---

## 🔄 Update Node

To update `synchronizer-cli`:

```bash
npm update -g synchronizer-cli
```

To pull the latest Docker image:

```bash
docker pull multisynq/synchronizer:latest
```

---

## 🧯 Logs & Troubleshooting

View logs using:

```bash
journalctl -u synchronizer-cli -f
journalctl -u synchronizer-cli-web -f
```

Stop services:

```bash
sudo systemctl stop synchronizer-cli synchronizer-cli-web
```

---

## 🛡️ Security Tips

* Change the default dashboard password after setup.
* Use a firewall or reverse proxy (e.g. Nginx) with TLS for public access.
* Avoid sharing your Synq Key or wallet publicly.

---

## 🙌 Join Community

Join TG : [WwCf Airdrop Telegram](https://t.me/WwCfAirdrops) 

Follow X : [WwCf Airdrop Twitter](https://x.com/WwCfOfficial) 

Subscribe : [WwCf Airdrop Youtube](https://youtube.com/@WwCfOfficial)

---

