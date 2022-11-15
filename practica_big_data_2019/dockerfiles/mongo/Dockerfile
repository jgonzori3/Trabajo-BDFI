FROM ubuntu:20.04
WORKDIR /app

RUN apt-get update 
RUN	apt-get upgrade -y 

RUN apt install wget -y

RUN apt update
RUN apt install gnupg -y
RUN wget -qO - https://www.mongodb.org/static/pgp/server-4.4.asc | apt-key add -

RUN apt-get install systemd -y

RUN echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-4.4.list

RUN apt install -y mongodb-org

RUN systemctl enable --now mongod

RUN apt update

RUN apt-get install git -y 

RUN	git clone https://github.com/jgonzori3/Trabajo-BDFI.git

# Copiamos el directorio en /app/practica_big_data_2019
RUN	mv Trabajo-BDFI/practica_big_data_2019 . 

WORKDIR /app/practica_big_data_2019


COPY . /app/practica_big_data_2019

RUN chmod +x ./start.sh

CMD ./start.sh
