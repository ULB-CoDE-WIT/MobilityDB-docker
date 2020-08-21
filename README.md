MobilityDB Docker
==================================

<img src="https://raw.githubusercontent.com/MobilityDB/MobilityDB/master/doc/images/mobilitydb-logo.svg" width="200" alt="MobilityDB Logo" />

[MobilityDB](https://github.com/MobilityDB/MobilityDB) is an open source software program that adds support for temporal and spatio-temporal objects to the [PostgreSQL](https://www.postgresql.org/) object-relational database and its spatial extension [PostGIS](http://postgis.net/).

This is a repository to hold various Docker images for MobilityDB releases. The images are based on the official [Postgres](https://github.com/docker-library/postgres) and [Postgis](https://github.com/postgis/docker-postgis) docker images so the documentation for the images also applies here, including the environment variables one can set, extensibility, etc.

Quick Start
-----------------

* Clone or download this repository
* Go inside the required version `cd 12-2.5-develop`
* Run this command `docker-compose up -d`

Then, you can connect directly with psql if you have the PostgreSQL client tool on your machine:
```
psql -h localhost -p 5432 -d mobilitydb -U docker
```
Otherwise, connect with psql using the container:
* Get the created container
	```
	docker ps
	```
* Enter inside the container
	```
	docker exec -it <container_name> bash
	```
* Connect with psql
	```
	psql -d mobilitydb -U docker
	```

Environment
-----------------
* `POSTGRES_DB` the default value is **mobilitydb**
* `POSTGRES_USER` the default value is **docker**
* `POSTGRES_PASSWORD` the default value is **docker**

Access to PgAdmin
-----------------
* **Host name/address** `localhost`
* **Port** `5432`
* **Username** as `POSTGRES_USER`, by default: `docker`
* **Password** as `POSTGRES_PASSWORD`, by default `docker`
