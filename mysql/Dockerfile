# ============================
# PULL OFFICIAL MYSQL REPO
# ============================
FROM mysql:5.7

# Fix permissions
RUN usermod -u 1000 mysql
RUN groupmod -g 1000 mysql

RUN chown -R mysql:mysql /var/run/mysqld
RUN chown -R mysql:mysql /var/log/mysql

ADD ./config/mysql/my.cnf /etc/mysql/conf.d/
