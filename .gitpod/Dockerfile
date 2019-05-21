FROM aspendigital/octobercms:develop

# create 'gitpod' user: It is used for everything that runs inside Gitpod workspaces
RUN useradd -l -u 33333 -G sudo -md /home/gitpod -s /bin/bash -p gitpod gitpod
ENV HOME=/home/gitpod
WORKDIR $HOME

# set app variables -  https://github.com/aspendigital/docker-octobercms#app-environment
ENV CMS_LINK_POLICY=secure \
    CMS_BACKEND_FORCE_SECURE=true

# configure Apache webserver for October in Gitpod
RUN echo "ServerName \${APACHE_SERVER_NAME}" >> /etc/apache2/apache2.conf && \
    chown -R gitpod:gitpod /etc/apache2 /var/run/apache2 /var/lock/apache2 /var/log/apache2 && \
    rm /var/log/apache2/*
COPY --chown=gitpod:gitpod apache/ /etc/apache2/
