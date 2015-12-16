FROM amacgregor/docker-phpfpm:base
MAINTAINER Allan MacGregor <amacgregor@allanmacgregor.com>

# Copy the custom configuration files
COPY config/phpfarm/src /opt/phpfarm/src/

# Compile, then delete sources (saves space)
RUN cd /opt/phpfarm/src && ./compile.sh 7.0.0 && \
rm -rf /opt/phpfarm/src && \
apt-get clean && \
rm -rf /var/lib/apt/lists/*

# Setup the PHPfpm services
COPY config/etc/init /etc/init/
COPY config/phpfarm/php-7.0.0/etc/php-fpm.conf /opt/phpfarm/inst/php-7.0.0/etc/

# Create the run scripts
RUN mkdir -p /opt/scripts/
ADD scripts/start-phpfpm-7.0.0.sh /opt/scripts/start-phpfpm-7.0.0.sh

# Supervisord Configuration
ADD config/supervisord-phpfpm7.0.conf /etc/supervisor/conf.d/supervisord-phpfpm7.0.conf

RUN usermod -u 501 www-data

RUN chmod 755 /opt/scripts/*.sh
ADD run.sh /run.sh
RUN chmod 755 /*.sh
CMD ["/run.sh"]
