# ============================
# SETUP BUILD ARGS
# ============================
ARG MYSQL_VERSION=5.7

# ============================
# PULL OFFICIAL PHP REPO
# ============================
FROM mysql:${MYSQL_VERSION}

# Fix permissions
RUN usermod -u 1000 mysql
RUN groupmod -g 1000 mysql

RUN chown -R mysql:mysql /var/run/mysqld
RUN chown -R mysql:mysql /var/log/mysql

ADD ./etc/mysql/my.cnf /etc/mysql/conf.d/
