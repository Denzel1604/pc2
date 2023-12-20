# Practica Creativa 2
## 1. Despliegue de la aplicación en máquina virtual pesada (2 puntos)
Creamos Instancia de VM en Google Cloud
-Version: Ubuntu 20.04
-Firewall: permitir todo el tráfico 
-Resto: default
En VM:
1. Actualizamos con:
```
sudo apt update
```
```
sudo apt upgrade
```
```
sudo apt install python3-pip
```

2. Clonamos repositorio de CDPS:
```
git clone https://github.com/CDPS-ETSIT/practica_creativa2.git
```
```
cd practica_creativa2/
```
3. Corregimos versiones e instalamos el requirements.txt 
- gevent==23.9.1
- greenlet==3.0.2
- urllib3==1.21.1
- testresources==2.0.1 (añadir)
```
vi bookinfo/src/productpage/requirements.txt
```
```
pip3 install -r bookinfo/src/productpage/requirements.txt
```

4. Cambiamos el titulo de la pagina por la variable de entorno GRUPO_NUMERO

***  FALTA ***

5. Lanzamos la aplicacion monolítica
```
python3 bookinfo/src/productpage/productpage_monolith.py 9080
```
## 2. Despliegue de una aplicación monolítica usando docker (2 puntos).

1. Instalación de Docker y Docker-Compose

```
sudo apt install docker.io
```
```
sudo apt install docker-compose
```

2. Definimos fichero Dockerfile en el directorio productpage
3. Montamos fichero Dockerfile
```
docker build -t 09/product-page .
```
```
docker run -p 9080:9080 09/product-page
```
4. 
