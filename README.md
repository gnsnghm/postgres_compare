# PostgreSQL version archive and compare for gnsnghm

PostgreSQL provides older versions on docker hub, but it is inefficient because you have to configure the config file every time.

So, I created my own Dockerfile so that I can quickly compare different versions and use them immediately.

## How to use

1. `git pull xxx`
1. Go to the directory of the version you want to build.
1. `docker build -t [docker name] .`
1. `docker run -p 5432:5432 --name [container name] -e POSTGRES_PASSWORD=[PASSWORD] -d [docker name]`

## Example

### Build Dockerfile

`docker build -t gnsnghm-postgresql:96 .`

### Run docker file

`docker run -p 5434:5432 --name gnsnghm-postgresql96 -e POSTGRES_PASSWORD=postgres00 -d gnsnghm-postgresql:96`

Notice:If port 5432 is already in use on the originating OS, change the port number.

## Remarks

### I want to change config file other than pg_hba.conf and postgresql.conf

You can edit it by entering the console using docker exec.

1. `docker exec -it [container name] /bin/bash`
1. If you want to change pg_data file, `cd /var/lib/pgsql/data`
