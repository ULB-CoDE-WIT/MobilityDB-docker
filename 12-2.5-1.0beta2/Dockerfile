FROM postgis/postgis:12-2.5
LABEL maintainer="MobilityDB Project - https://github.com/MobilityDB/MobilityDB"
ENV MOBILITYDB_VERSION 1.0-beta2
ENV POSTGRES_DBNAME=mobilitydb
ENV POSTGRES_USER=docker 
ENV POSTGRES_PASSWORD=docker

# Fix the Release file expired problem
RUN echo "Acquire::Check-Valid-Until \"false\";\nAcquire::Check-Date \"false\";" | cat > /etc/apt/apt.conf.d/10no--check-valid-until

# Install Prerequisites 
RUN apt-get update \
 && apt-get install -y \
    build-essential \
    cmake \
    wget \
    libpq-dev \
    liblwgeom-dev \
    libproj-dev \
    libjson-c-dev \
    libgsl-dev \
    libgslcblas0 \    
    postgresql-server-dev-12 \
 && wget -O MobilityDB.tar.gz "https://github.com/MobilityDB/MobilityDB/archive/v${MOBILITYDB_VERSION}.tar.gz" \
 && mkdir -p /usr/local/src/MobilityDB \
 && tar \
        --extract \
        --file MobilityDB.tar.gz \
        --directory /usr/local/src/MobilityDB \
        --strip-components 1 \
 && rm MobilityDB.tar.gz
RUN mkdir /usr/local/src/MobilityDB/build
RUN cd /usr/local/src/MobilityDB/build && \
	cmake .. && \
	make -j$(nproc) && \
	make install

RUN rm /docker-entrypoint-initdb.d/10_postgis.sh
COPY ./initdb-mobilitydb.sh /docker-entrypoint-initdb.d/
RUN chmod +x /docker-entrypoint-initdb.d/initdb-mobilitydb.sh
