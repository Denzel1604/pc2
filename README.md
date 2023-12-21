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
git clone https://github.com/Denzel1604/pc2.git
```
```
cd pc2/
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

2. Obtenemos el fichero Dockerfile
```
git clone https://github.com/Denzel1604/pc2.git
```
```
cp pc2/docker/productpage/Dockerfile .
```
```
rm -rf pc2/
```


3. Montamos fichero Dockerfile
```
sudo docker build -t 09/product-page .
```
```
sudo docker run -p 9080:9080 09/product-page
```


## 3. Segmentación de una aplicación monolítica en microservicios utilizando docker-compose ( 2 puntos)

1. Montamos cada imagen Dockerfile
```
git clone https://github.com/Denzel1604/pc2.git
```

Details
```
cp pc2/docker/details/Dockerfile .
```
```
sudo docker build -t 09/details .
```

Ratings
```
cp pc2/docker/ratings/Dockerfile .
```
```
sudo docker build -t 09/ratings .
```

Reviews

```
cd pc2/bookinfo/src/reviews
```
```
sudo docker run --rm -u root -v "$(pwd)":/home/gradle/project -w /home/gradle/project gradle:4.8.1 gradle clean build
```
```
cd reviews-wlpcfg
```
```
sudo docker build -t 09/reviews:v1 --build-arg service_version=v1 --build-arg enable_ratings=true  .
```

```
sudo docker build -t 09/reviews:v2 --build-arg service_version=v2 --build-arg enable_ratings=true  .
```

```
sudo docker build -t 09/reviews:v3 --build-arg service_version=v3 --build-arg enable_ratings=true  .
```

```
cd 
```

2. Obtenemos el fichero docker-compoes.yaml

```
cp pc2/docker/docker-compose.yaml .
```
```
rm -rf pc2/
```

3. Lanzamos docker-compose

```
sudo docker-compose up -d
```
