FROM debian:12

RUN apt update
RUN apt install apt-transport-https lsb-release ca-certificates wget curl -y
RUN curl -sSLo /tmp/debsuryorg-archive-keyring.deb https://packages.sury.org/debsuryorg-archive-keyring.deb
RUN dpkg -i /tmp/debsuryorg-archive-keyring.deb
RUN sh -c 'echo "deb [signed-by=/usr/share/keyrings/deb.sury.org-php.gpg] https://ftp.mpi-inf.mpg.de/mirrors/linux/mirror/deb.sury.org/repositories/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list'
RUN apt update && \
    apt upgrade -y

RUN apt install -y unzip apache2 php8.2 php8.2-mysql php8.2-ldap php8.2-mcrypt php8.2-cli php8.2-soap php8.2-xml php8.2-gd php8.2-zip php8.2-simplexml php8.2-dom php8.2-mbstring php8.2-curl graphviz libapache2-mod-php

COPY php.ini /usr/lib/php/8.2/apache2/

WORKDIR /var/www/html/

RUN rm index.html
RUN wget https://sourceforge.net/projects/itop/files/itop/3.1.2/iTop-3.1.2-14913.zip
RUN unzip iTop-3.1.2-14913.zip
RUN mkdir conf data env-production env-production-build log
RUN mv web/* .
RUN chown www-data:www-data /var/www/html/* -R
RUN rm iTop-3.1.2-14913.zip


EXPOSE 80
CMD ["/usr/sbin/apachectl", "-D", "FOREGROUND"]