FROM proboci/ubuntu:14.04

ENV MYSQL_USER=mysql \
    MYSQL_VERSION=5.5 \
    MYSQL_DATA_DIR=/var/lib/mysql \
    MYSQL_RUN_DIR=/run/mysqld \
    MYSQL_LOG_DIR=/var/log/mysql

RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get install -y mysql-server-${MYSQL_VERSION} \
 && rm -rf ${MYSQL_DATA_DIR} \
 && rm -rf /var/lib/apt/lists/*

EXPOSE 3306/tcp
