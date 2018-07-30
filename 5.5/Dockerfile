FROM proboci/apache:2.4

ENV MYSQL_USER=mysql \
    MYSQL_VERSION=5.5 \
    MYSQL_DATA_DIR=/var/lib/mysql \
    MYSQL_RUN_DIR=/run/mysqld \
    MYSQL_LOG_DIR=/var/log/mysql

RUN export DEBIAN_FRONTEND=noninteractive
ENV MYSQL_ROOT_PASS strongpassword
COPY .my.cnf /root/.my.cnf
RUN echo "mysql-server mysql-server/root_password password ${MYSQL_ROOT_PASS}" | debconf-set-selections  && \
        echo "mysql-server mysql-server/root_password_again password ${MYSQL_ROOT_PASS}" | debconf-set-selections && \
        apt-get -q -y install mysql-server-${MYSQL_VERSION} python-mysqldb \
 && chown -R mysql:mysql /var/lib/mysql/mysql \
 && rm -rf /var/lib/apt/lists/*
RUN find /var/lib/mysql -type f -exec touch {} \; && service mysql stop

EXPOSE 3306/tcp
VOLUME /var/lib/mysql
