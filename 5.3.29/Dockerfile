FROM amacgregor/docker-phpfpm:base
MAINTAINER Allan MacGregor <amacgregor@allanmacgregor.com>

# Copy the custom configuration files
COPY config/phpfarm/src /opt/phpfarm/src/

### Special Instructions for 5.3
RUN wget https://www.openssl.org/source/openssl-0.9.8zb.tar.gz && \
tar -xzvf openssl-0.9.8zb.tar.gz && \
cd openssl-0.9.8zb && \
make && make install 

# Compile, then delete sources (saves space)
RUN cd /opt/phpfarm/src && ./compile.sh 5.3.29 && \
rm -rf /opt/phpfarm/src && \
apt-get clean && \
rm -rf /var/lib/apt/lists/*

# Setup the PHPfpm services
COPY config/etc/init /etc/init/
COPY config/phpfarm/php-5.3.29/etc/php-fpm.conf /opt/phpfarm/inst/php-5.3.29/etc/

# Create the run scripts
RUN mkdir -p /opt/scripts/
ADD scripts/start-phpfpm-5.3.29.sh /opt/scripts/start-phpfpm-5.3.29.sh

# Supervisord Configuration
ADD config/supervisord-phpfpm5.3.conf /etc/supervisor/conf.d/supervisord-phpfpm5.3.conf

RUN chmod 755 /opt/scripts/*.sh
ADD run.sh /run.sh
RUN chmod 755 /*.sh
CMD ["/run.sh"]
