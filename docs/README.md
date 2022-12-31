```shell
mvn package

cd docker
docker-compose up
docker-compose up -d
docker-compose up -d mall4j-redis
docker-compose down

docker-compose build

docker-compose ps
docker-compose logs -f

mysql -h127.0.0.1 -uroot -p -P3317
mysql -h127.0.0.1 -uroot -p -P3317 < db/yami_shop.sql

https://m-admin.7otech.com
https://m-admin.7otech.com/apis
https://m-api.7otech.com
```

```shell
docker-compose ps
    Name                  Command                 State                             Ports
----------------------------------------------------------------------------------------------------------------
mall4j-admin   /bin/sh -c java -jar -Xms5 ...   Restarting
mall4j-api     /bin/sh -c java -jar -Xms1 ...   Up           0.0.0.0:8086->8086/tcp,:::8086->8086/tcp
mall4j-mysql   docker-entrypoint.sh --low ...   Up           0.0.0.0:3317->3306/tcp,:::3317->3306/tcp, 33060/tcp
mall4j-redis   docker-entrypoint.sh redis ...   Up           0.0.0.0:6379->6379/tcp,:::6379->6379/tcp
```

```
address: redis://${REDIS_HOST}:${REDIS_PORT}
  database: ${REDIS_DATABASE}
  password: ${REDIS_PASSWORD}

url: jdbc:mysql://${MYSQL_HOST:mall4j-mysql}:${MYSQL_PORT:3306}/${MYSQL_DATABASE:yami_shops}?allowMultiQueries=true&useSSL=false&useUnicode=true&characterEncoding=UTF-8&autoReconnect=true&zeroDateTimeBehavior=convertToNull&useJDBCCompliantTimezoneShift=true&useLegacyDatetimeCode=false&serverTimezone=GMT%2B8&nullCatalogMeansCurrent=true
    username: ${MYSQL_USERNAME:root}
    password: ${MYSQL_PASSWORD:root}
```