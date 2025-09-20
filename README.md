# NAS Services Docker Standup

---
This is a simple docker-compose configuration to run some base services on a Synology NAS.

## Services

- [Portainer](https://www.portainer.io/) - for managing docker containers
- [Speedtest-Tracker](https://docs.speedtest-tracker.dev/) - for tracking your internet speed
- [Cloudflared](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/) - for access management
- [Watchtower](https://github.com/containrrr/watchtower) - for automated container updates

## Install Instructions

### Prerequisites

- Synology NAS
- [Git](https://git-scm.com/)
- [Docker](https://www.docker.com/)
- [Docker-Compose](https://docs.docker.com/compose/)

### Server Configuration

1. Setup Synology NAS and [install DSM](https://www.synology.com/en-us/knowledgebase/DSM/tutorial/General_Setup/How_to_install_DSM)
1. Install [Docker](https://www.synology.com/en-us/dsm/packages/Docker) via Add-on Packages
1. Add the SynoCommunity package source via [easy install](https://synocommunity.com/#easy-install)
1. Install Git package from SynoCommunity
1. Enable SSH Access
1. Create Docker Group and Add User

```plaintext
- create the group "docker" from the ui or cli (sudo synogroup --add docker)
- make it the group of the docker.sock: sudo chown root:docker /var/run/docker.sock
- assign the user to the docker group in the ui or cli (sudo synogroup --member docker {username})
- login into ssh as {username} and try (if you were already logged in before you created the group, logout and relogin)
```

1. Make sure DSM isn't using 80/443 with [guide](https://www.smarthomebeginner.com/synology-docker-media-server/#8_Ensure_Ports_80_and_443_are_Free)

Make a scheduled task of those commands

1. Clone Repo `git clone https://gitlab.com/thinkonezero/services-docker-standup.git`
1. Copy Sample Environement File `cp sample.env .env`
1. Edit `.env` to match your environment
1. Run Docker Environment `docker-compose up -d`
1. ???
1. Profit.

### Environment File

```plaintext
LOCALUSER=
HOSTNAME=
PUID=
PGID=
TZ=
LOG_FILE_NUM=5
LOG_FILE_SIZE=10m
LOCAL_DOMAIN=
CLOUDFLARED_TOKEN=
STACK_NAME=
BASE_DOCKER_PATH=/volume1/docker
SMTP_SERVER=mail.example.com
SMTP_PORT=587
SMTP_LOGIN=
SMTP_PASSWORD=
SMTP_FROM_ADDRESS=notifications@example.com
WATCHTOWER_NOTIFICATIONS=email
WATCHTOWER_NOTIFICATION_EMAIL_TO=me@example.com
PORTAINER_PORT=9000
SPEEDTEST_PORT=8080
SPEEDTEST_APP_KEY=
SPEEDTEST_APP_URL=
SPEEDTEST_ASSET_URL=
SPEEDTEST_SCHEDULE=6 */2 * * *
```

### Email/SMTP Service

- [Mailgun](https://documentation.mailgun.com/en/latest/quickstart.html) has an excellent QuickStart Guide
- Check out the sending via [SMTP](https://documentation.mailgun.com/en/latest/quickstart-sending.html#send-via-api)
- Make sure to also [verify your domain](https://documentation.mailgun.com/en/latest/quickstart-sending.html#verify-your-domain)

---

## Tips and Tricks

- [Proper Encoding of the Portainer Password](https://github.com/portainer/portainer/issues/1506)
- Open Shell in a Container - [Link 1](http://phase2.github.io/devtools/common-tasks/ssh-into-a-container/), [Link 2](https://stackoverflow.com/a/30173220)

---

If this project has helped you in anyway, and you'd like to say thanks...

[![Donate](https://img.shields.io/badge/Donate-SquareCash-brightgreen.svg)](https://cash.me/$phikai)

_AFFILIATE DISCLOSURE: You can also support this project by purchasing a VPN Subscription via one of the links in this README._

---

# Disclaimer

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
