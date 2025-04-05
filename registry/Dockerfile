FROM mysql:9.0

COPY ./sql-scripts/ /docker-entrypoint-initdb.d/

ENV MYSQL_ROOT_PASSWORD=root
ENV MYSQL_DATABASE=bypass
ENV MYSQL_USER=bypass
ENV MYSQL_PASSWORD=bypass123

EXPOSE 3306
