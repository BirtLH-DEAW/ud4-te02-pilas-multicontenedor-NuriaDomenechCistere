FROM ubuntu:18.04

RUN apt-get update && apt-get install -y apache2 \
    && apt-get install -y libapache2-mod-fcgid \
    && a2enmod proxy_fcgi \
    && apt-get install -y git

RUN git clone https://github.com/deaw-birt/UD4-despliegue-PHP /tmp/repo

RUN cp -r /tmp/repo/php/* /var/www/html/

RUN rm -rf /tmp/repo

COPY 000-default.conf /etc/apache2/sites-available/

WORKDIR /var/www/html

RUN chown -R www-data:www-data /var/www/html && \
    chmod -R 755 /var/www/html

EXPOSE 80

CMD ["apachectl", "-D", "FOREGROUND"]
