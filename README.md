# rcloneqbit 🚀

[![Docker Pulls](https://img.shields.io/docker/pulls/rclone/rclone)](https://hub.docker.com/r/eloyn/rcloneqbit)

Este contenedor de docker contiene el cliente qBittorrent y la herramienta Rclone, con la finalidad de automatizar la subida de nuestras descargas a los principales servidores cloud como gdrive etc.

### Pre-requisitos 📋
Únicamente necesitaremos tener docker instalado en nuestro sistema operativo.

## Despliegue 📦
La forma más recomendades para lanzar este contenedor es la siguiente:

```
docker run \
  --name=qbittorrent \
  -e PUID=1000 \
  -e PGID=1000 \
  -e TZ=Europe/London \
  -e UMASK_SET=022 \
  -e WEBUI_PORT=8080 \
  -p 6881:6881 \
  -p 6881:6881/udp \
  -p 8085:8080 \
  -v /tupath/config:/config \
  -v /tupath/downloads:/downloads \
  --restart unless-stopped \
-it eloyn/rcloneqbit /bin/bash
```
## +info 📖
La versión que contiene del cliente qBittorrent es la v4.1.9

Es necesario que las carpetas a las cuáles apuntan los volúmenes tengan permisos de escritura y lectura de lo contrario rclone no podrá leer y escribir su fichero de configuración.
