#CRIAÇÃO DE APLICATIVO WEB NO DOCKER
mkdir servidor-apache // primeiro criamos a pasta onde ficara
cd servidor-apache // mudamos o diretorio para dentro da pasta que criamos
mkdir site // criamos a pasta do site
o dockerfile vai ficar como abaixo
FROM debian
RUN apt-get update && apt-get install -y apache2 && apt-get clean
ENV APACHE LOCK DIR="var/lock"
ENV APACHE_PID_FILE="var/run/apache2.pid"
ENV APACHE_RUN_USER="www-data"
ENV APACHE_RUN_GROUP="www-data"
ENV APACHE_LOG_DIR=/var/log/apache2"
add site.tar /var/www/html
LABEL description="Apache webserver 1.0"
VOLUME /var/www/html // onde será salvo
EXPOSE 80 / a porta que usará
ENTRYPOINT ["/usr/sbin/apachectl"] qual aplicação rodará
CMD ["-D", "FOREGROUND"] //apachectl executado em primeiro plano
depois de fazer o dockerfile, no terminal escrever os comandos
docker image build -t servidor-apache:1.0 . // após os dois pontos é a tag da versão