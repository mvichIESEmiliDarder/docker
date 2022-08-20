# Docker
Install, configuration an setting up docker

## Instal·lam docker
Donam per suposat que durant la instal·lació de *Ubuntu Server* hem triat l'opció d'instal·lar *docker*

## Instal·lam docker-compose
````bash
mkdir -p ~/.docker/cli-plugins/
````
:warning: Hem de descarregar la versió que pertoqui de docker. Podem trobar-la a [Docker-Compose](https://github.com/docker/compose/releases). En aquest cas hem davallat la **v.2.10**
```bash
curl -SL https://github.com/docker/compose/releases/download/v2.10/docker-compose-linux-x86_64 -o ~/.docker/cli-plugins/docker-compose
chmod +x ~/.docker/cli-plugins/docker-compose
docker-compose version
````

## Instal·lam portainer
:warning: Hem de descarregar la versió que pertoqui de portainer. Podem trobar-la a [Portainer](https://github.com/portainer/portainer/releases/). En aquest cas hem davallat la **v.2.14.2**
```bash
docker run -d -p 8000:8000 -p 9443:9443 --name portainer \
    --restart=always \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v portainer_data:/data \
    portainer/portainer-ce:2.14.2
```
Configuram portainer anant a la pàgina del servidor on l'hem instal·lat: **https://'ip':9443**
- Introduïm la contrasenya de l'usuari administrador
- Començam amb *Getting started*

