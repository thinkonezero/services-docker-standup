# services-docker-standup

## Getting started

Environment Variables:

```plaintext
### 
###  --------------------------------------------------------------
###  S E R V I C E S - D O C K E R   C O N F I G   S E T T I N G S
###  ---------------------------------------------------------------
###  The values configured here are applied during
###  $ docker-compose up
###  -----------------------------------------------
###  DOCKER-COMPOSE ENVIRONMENT VARIABLES BEGIN HERE
###  -----------------------------------------------
###

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
```
