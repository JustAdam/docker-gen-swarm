# docker-gen and Docker Swarm

The is an example of connecting docker-gen to a Docker Swarm cluster.  Please see [this](http://www.before.no/2015/04/using-docker-gen-with-a-swarm-cluster/) post for more details.

## Before starting

* Place a `docker-gen` binary in the `docker-gen/` folder.
* Copy the SSL certificates for your Docker Swarm master into the `docker-gen/certs` folder.
* Update the default site configuration for the nginx reverse proxy (see `docker-gen/sites-enabled/default`)
* Update the **DOCKER_HOST** environment variable in `docker-compose.yml` to point to the correct address of the Swarm master.

```
$ docker-compose up -d
```