FROM mysql:oracle

COPY ./products.csv /products.csv
COPY ./users.csv /users.csv
COPY ./setup.sql /docker-entrypoint-initdb.d/setup.sql

ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["mysqld", "--secure-file-priv=/"]
#CMD ["--secure-file-priv=/"]
