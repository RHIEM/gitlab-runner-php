FROM gitlab/gitlab-runner
LABEL maintainer="markus.lach@rhiem.com"
RUN apt-get update \
    && apt-get install -y software-properties-common
RUN add-apt-repository ppa:ondrej/php -y
RUN apt-get update
RUN apt-get install -y php7.2-cli \
    php7.2-gd \
    php7.2-zip \
    php7.2-intl \
    php7.2-pdo-mysql \
    php7.2-mbstring \
    php7.2-xml \
    php7.2-curl
RUN apt-get update \
    && apt-get install -y rsync vim
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

STOPSIGNAL SIGQUIT
VOLUME ["/etc/gitlab-runner", "/home/gitlab-runner"]
ENTRYPOINT ["/usr/bin/dumb-init", "/entrypoint"]
CMD ["run", "--user=gitlab-runner", "--working-directory=/home/gitlab-runner"]
