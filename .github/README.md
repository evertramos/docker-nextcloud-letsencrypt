# Automated docker nextcloud for nginx proxy (webproxy) integrated with LetsEncrypt

This repo allows you  to set up the great [Nextcloud](https://nextcloud.com) as a container over SSL auto generated and auto renewed by our Web Proxy.

![Nextcloud Environment](https://github.com/evertramos/images/raw/master/nextcloud.jpg)

# Prerequisites

In order to use this compose file (docker-compose.yml) you must have:

1. docker [https://docs.docker.com/engine/installation/](https://docs.docker.com/engine/installation/)
2. docker-compose [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)
3. docker-compose-letsencrypt-nginx-proxy-companion [https://github.com/evertramos/docker-compose-letsencrypt-nginx-proxy-companion](https://github.com/evertramos/docker-compose-letsencrypt-nginx-proxy-companion)

# How to use

1. Clone this repository:

```bash
git clone https://github.com/evertramos/docker-nextcloud-letsencrypt.git
```

2. Make a copy of our .env.sample and rename it to .env:

Update this file with your preferences.

```bash
#
# Configuration for Nextcloud using NGINX WebProxy
#

# Containers name
DB_CONTAINER_NAME=cloud-db
APP_CONTAINER_NAME=cloud-app

# Mysql settings
MYSQL_HOST=cloud-db
MYSQL_DATABASE=cloud_db
MYSQL_ROOT_PASSWORD= cloud,root,password
MYSQL_USER=cloud_user
MYSQL_PASSWORD=cloud,user,password

# Nextcloud settings
NEXTCLOUD_ADMIN_USER=admin
NEXTCLOUD_ADMIN_PASSWORD=admin,password

# Nextcloud data path
NEXTCLOUD_DATA_DIR=/var/www/html/data
NEXTCLOUD_TABLE_PREFIX=

# Nextcloud local data path
LOCAL_DB_DIR=/home/user/cloud/data/db
LOCAL_DATA_DIR=/home/user/cloud/data/cloud
LOCAL_CONF_DIR=/home/user/cloud/data/cloud/config
LOCAL_APPS_DIR=/home/user/cloud/data/cloud/apps

# Host 
VIRTUAL_HOST=cloud.yourdomain.com
LETSENCRYPT_HOST=cloud.yourdomain.com
LETSENCRYPT_EMAIL=your_email@yourdomain.com

#
# Network name
# 
# Your container app must use a network conencted to your webproxy 
# https://github.com/evertramos/docker-compose-letsencrypt-nginx-proxy-companion
#
NETWORK=webproxy
```

3. Start your container

```bash
# docker-compose up -d
```

> This container must be in a network connected to your webproxy containers or use the same network of the webproxy.

> Please keep in mind that when starting for the first time it may take a few moments (even a couple minutes) to get your Let's Encrypt certificates generated.

### Any further Nextcloud configuration please check [Nextcloud Admin Documentation](https://docs.nextcloud.com/server/12/admin_manual/)
