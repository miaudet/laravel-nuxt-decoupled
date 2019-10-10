FROM cstipulaval/web_php7.2:latest

ADD apache-config.conf /etc/apache2/sites-enabled/000-default.conf
ADD apache-config-ssl.conf /etc/apache2/sites-available/default-ssl.conf

RUN sed -i "s/xdebug.remote_host/xdebug.remote_host = 132.203.224.163/" /etc/php/7.2/apache2/php.ini