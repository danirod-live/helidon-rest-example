# ejemplo-helidon

Helidon MP application that uses the dbclient API with MySQL database.

## Build and run


This example requires a MySQL database, start it using docker:

```
docker run --rm --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=pokemon -e MYSQL_USER=user -e MYSQL_PASSWORD=password  mysql:5.7
```


With JDK17+
```bash
mvn package
java -jar target/ejemplo-helidon.jar
```

## Exercise the application
```
curl -X GET http://localhost:8080/simple-greet
{"message":"Hello World!"}
```



## Try metrics

```
# Prometheus Format
curl -s -X GET http://localhost:8080/metrics
# TYPE base:gc_g1_young_generation_count gauge
. . .

# JSON Format
curl -H 'Accept: application/json' -X GET http://localhost:8080/metrics
{"base":...
. . .
```



## Try health

```
curl -s -X GET http://localhost:8080/health
{"outcome":"UP",...

```



## Building the Docker Image

```
docker build -t ejemplo-helidon .
```

## Running the Docker Image

```
docker run --rm -p 8080:8080 ejemplo-helidon:latest
```

Exercise the application as described above.
                                
