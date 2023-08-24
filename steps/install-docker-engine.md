# Instalar Docker Engine

> Para la instalación se tendrá en cuenta lo especificado en la [documentación de Docker](https://docs.docker.com/engine/install/ubuntu/) por lo que en caso de presentar algun inconveniente puede remitirse a esa documentación.

## Limpiar dependencias y eliminar paquetes y archivos viejos

Ejecute en la `terminal de ubuntu` los siguientes comandos:

~~~bash
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done
~~~

~~~bash
sudo apt-get purge docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-ce-rootless-extras
~~~

~~~bash
sudo rm -rf /var/lib/docker
~~~

~~~bash
sudo rm -rf /var/lib/containerd
~~~

## Configurar repositorio de docker

Ejecute en la `terminal de ubuntu` los siguientes comandos:

~~~bash
sudo apt-get update
~~~

~~~bash
sudo apt-get install ca-certificates curl gnupg
~~~

~~~bash
sudo install -m 0755 -d /etc/apt/keyrings
~~~

~~~bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
~~~

~~~bash
sudo chmod a+r /etc/apt/keyrings/docker.gpg
~~~

~~~bash
echo "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
~~~

~~~bash
sudo apt-get update
~~~

## Instalar paquetes de Docker

Ejecute en la `terminal de ubuntu` los siguientes comandos:

~~~bash
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
~~~

## Configurar Tablas de enrutamiento

Ejecute en la `terminal de ubuntu` el siguiente comando y seleccione la opción referenciada como `iptables-legacy`

~~~bash
sudo update-alternatives --config iptables
~~~

Realizado el ajuste inicie el servicio de docker con el siguiente comando

~~~bash
sudo service docker start
~~~

Puede probar que docker haya quedado correctamente iniciado ejecutando el siguiente comando

~~~bash
sudo docker run hello-world
~~~

## Configurar acceso al servicio de Docker

Ejecute en la `terminal de ubunto` los siguientes comandos:

~~~bash
sudo groupadd docker
~~~

~~~bash
sudo usermod -aG docker $USER
~~~

~~~bash
newgrp
~~~

Puede probar que docker funcione correctamente ejecutando el siguiente comando

~~~bash
docker run hello-world
~~~

## Enlaces

- [Anterior: Aplicar configuración recomendada para GIT en máquina Linux](./setup-git-on-linux.md)
- [Instalación y configuración de WSL en Windows](../README.md)
