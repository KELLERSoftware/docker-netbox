# NetBox Dockerfile

This is a Dockerfile for [NetBox](https://github.com/digitalocean/netbox) the open-source web based IPAM and DCIM tool, nitially conceived by the network engineering team at DigitalOcean.
The image is based on debian with python 2.7 runs with nginx webserver as reverse-proxy and unicorn for the django app.

[![](https://images.microbadger.com/badges/image/kellersoftware/netbox.svg)](https://microbadger.com/images/kellersoftware/netbox)

It will:

* Install debian jessie as base system.
* Install python 2.7 with all required modules.
* Configure and install nginx as reverse proxy to serve web assets (html, css).
* Download the latest stable NetBox release from github.com.


## Building

```
$ git clone https://github.com/KELLERSoftware/docker-netbox.git
$ cd docker-netbox
$ docker build -t netbox .
```


## Run NetBox

To run NetBox is easy if you have a database, start the image with docker and provide some variables.
```
docker run -d -p 80 --name netbox --link postgres:postgres -e DB_NAME=netbox -e DB_USER=netbox -e DB_PASSWORD=123456 -e DB_HOST=postgres -e SECRET_KEY=123456 -e ALLOWED_HOSTS=netbox.company.com kellersoftware/netbox
```
Then, access it via [http://localhost](http://localhost) or [http://host-ip](http://host-ip) in a browser. Default login is admin/admin.


## Image on Docker Hub

This repro is linked to [Docker Hub](https://hub.docker.com/r/kellersoftware/) and will be build automatically. 


## Setup

```
Here are some instructions to setup and run netbox with the databse.
```


## Database

NetBox requires a PostgreSQL database to store data. (Please note that MySQL is not supported, as NetBox leverages PostgreSQL's built-in network address types.) There is no database inside this Docker container and you have to create empty db with user: [http://netbox.readthedocs.io/en/stable/installation/postgresql/#database-creation](http://netbox.readthedocs.io/en/stable/installation/postgresql/#database-creation).


