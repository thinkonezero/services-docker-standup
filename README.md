# NAS Services Docker Standup

This configuration deploys essential maintenance and infrastructure services for your Synology NAS Docker environment.

## 🚀 Services

| Service | Description |
| :--- | :--- |
| [Portainer](https://www.portainer.io/) | A powerful UI for managing Docker containers, images, and stacks. |
| [Speedtest-Tracker](https://docs.speedtest-tracker.dev/) | Automatically runs speed tests and graphs your internet performance over time. |
| [Cloudflared](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/) | Connects your local services to the internet securely via Cloudflare Tunnels. |
| [Watchtower](https://github.com/containrrr/watchtower) | Automates the process of updating your running Docker containers. |

## 📋 Prerequisites

- Synology NAS (DSM 7.x recommended)
- [Git](https://git-scm.com/) installed via SynoCommunity
- [Docker / Container Manager](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

## 🛠️ Setup

1. **Clone the project**:
   ```bash
   git clone https://github.com/thinkonezero/services-docker-standup.git
   ```
2. **Environment Configuration**:
   - Copy `sample.env` to `.env`.
   - Update `BASE_DOCKER_PATH` to your docker root.
   - Configure `SMTP` settings if you want Watchtower to send update notifications.
3. **Deploy**:
   ```bash
   docker compose up -d
   ```

## 🌐 Accessing Apps

| App | Default URL |
| :--- | :--- |
| **Portainer** | `http://<NAS_IP>:${PORTAINER_PORT}` |
| **Speedtest** | `http://<NAS_IP>:${SPEEDTEST_PORT}` |

## ⚙️ Environment Variables

- `SPEEDTEST_SCHEDULE`: Cron-style schedule for tests (default: every 2 hours).
- `CLOUDFLARED_TOKEN`: Required for your Cloudflare Zero Trust tunnel.
- `WATCHTOWER_NOTIFICATIONS`: Set to `email` for update alerts.
- `WATCHTOWER_ROLLING_RESTART`: Set to `true` to update containers one at a time.
- `WATCHTOWER_TIMEOUT`: The time to wait for a container to stop gracefully before a forced kill (default: 60s).

---

If this project has helped you, please consider supporting my work!

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/G2G71SUNID)

---

# Disclaimer

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED. IN NO EVENT SHALL THE AUTHORS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY.