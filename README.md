## docker-maintenance
[![docker hub](https://img.shields.io/badge/docker_hub-link-blue?style=for-the-badge&logo=docker)](https://hub.docker.com/r/vcxpz/maintenance) ![docker image size](https://img.shields.io/docker/image-size/vcxpz/maintenance?style=for-the-badge&logo=docker) [![auto build](https://img.shields.io/badge/docker_builds-automated-blue?style=for-the-badge&logo=docker?color=d1aa67)](https://github.com/hydazz/docker-maintenance/actions?query=workflow%3A"Auto+Builder+CI") [![template](https://img.shields.io/badge/view_html_template-blue?style=for-the-badge)](https://htmlpreview.github.io/?https://github.com/hydazz/docker-maintenance/blob/main/root/defaults/index.html)

Barebones Nginx server specifically made to be a maintenance page for when your SWAG container is down or backing up. Theoretically, when you stop your SWAG container and spin this one up, it should just work. When you startup this image it will attempt to migrate from SWAG, and it works for me so whatever. You may need to change some settings in your configs for Nginx to start successfully.

If you have important proxy-confs, such as Home Assistant that you need to have 24/7 uptime, add `proxy-confs/homeassistant.<subdomain/subfolder>.conf` to /config/includes.txt and it will copy over to the maintenance appdata, and you will be able to access Home Assistant through this container. This works for any proxy config.

## Version Information
![alpine](https://img.shields.io/badge/alpine-edge-0D597F?style=for-the-badge&logo=alpine-linux) ![s6 overlay](https://img.shields.io/badge/s6_overlay-2.1.0.2-blue?style=for-the-badge) ![nginx](https://img.shields.io/badge/nginx-1.18.0-269539?style=for-the-badge&logo=nginx)

**[See here for a list of packages](https://github.com/hydazz/docker-maintenance/blob/main/package_versions.txt)**

## Usage
```
docker run -d \
  --name=maintenance \
  -e PUID=1000 \
  -e PGID=1000 \
  -e TZ=Australia/Melbourne \
  -p 443:443 \
  -p 80:80 \
  -v <path to appdata>:/config \
  -v <path to swag data>:/swag \
  --restart unless-stopped \
  vcxpz/maintenance
```
[![template](https://img.shields.io/badge/unraid_template-ff8c2f?style=for-the-badge&logo=docker?color=d1aa67)](https://github.com/hydazz/docker-templates/blob/main/hydaz/maintenance.xml)
