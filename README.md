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

## Instal·lam i configuram Apache des de portainer
- Anam a la pàgina https://'ip':9443
- App templates
- Httpd Container
  - En avançat, hem de cercar per mapejar el port 80 del contenidor a un altre port del servidor, p.e. el 8081

Així ja tindrem instal·lat Apache corrent al port 8081. Podem confirmar que funciona anant a http://'ip':8081.
Toca sortir la pantalla de **It works!**

:exclamation: Si volem activar el mòdul d'estadístiques farem:
- Dins el contenidor, ens ficam a la consola
- Instal·lam la comanda nano:
```bash
apt install nano
```
- Configuram correctament el modul status
```bash
cd conf
nano httpd.conf
```
Cercam que la linia *LoadModule status_module modules/mod_status.so* estigui descomentada
Afegim el següent al final del fitxer:
```yaml
<Location /server-status>
    SetHandler server-status
    Order allow,deny
    Allow from all
</Location>
```

