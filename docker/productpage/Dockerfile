FROM python:3.8.10

WORKDIR /app

RUN sudo apt update

RUN sudo apt upgrade

RUN sudo apt install python3-pip

RUN git clone https://github.com/Denzel1604/pc2.git

ENV GROUP_NUMBER 09

RUN pip3 install -r pc2/bookinfo/src/productpage/requirements.txt


## No hace falta exponer el puerto 9080 de esta manera porque solo lo habilita
## para la comunicacion entre containers (y solo tenemos uno)
#EXPOSE 9080

CMD ["python3", "pc2/bookinfo/src/productpage/productpage_monolith.py", "9080"]