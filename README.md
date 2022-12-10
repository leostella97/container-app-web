<h1>CRIAÇÃO DE APLICATIVO WEB NO DOCKER</h1>
<br>
mkdir servidor-apache // primeiro criamos a pasta onde ficara
<br>
cd servidor-apache // mudamos o diretorio para dentro da pasta que criamos
<br>
mkdir site // criamos a pasta do site
<br><br>
o dockerfile vai ficar como abaixo
<br>
FROM debian
<br>
RUN apt-get update && apt-get install -y apache2 && apt-get clean
<br>
ENV APACHE LOCK DIR="var/lock"
<br>
ENV APACHE_PID_FILE="var/run/apache2.pid"
<br>
ENV APACHE_RUN_USER="www-data"
<br>
ENV APACHE_RUN_GROUP="www-data"
<br>
ENV APACHE_LOG_DIR=/var/log/apache2"
<br>
add site.tar /var/www/html
<br>
LABEL description="Apache webserver 1.0"
<br>
VOLUME /var/www/html // onde será salvo
<br>
EXPOSE 80 / a porta que usará
<br>
ENTRYPOINT ["/usr/sbin/apachectl"] qual aplicação rodará
<br>
CMD ["-D", "FOREGROUND"] //apachectl executado em primeiro plano
<br>
depois de fazer o dockerfile, no terminal escrever os comandos
<br>
docker image build -t servidor-apache:1.0 . // após os dois pontos é a tag da versão