![logo](https://products.containerize.com/devops/compose/header_image.png)

# Final-docker-compose-YML on Lubuntu
Objective
The purpose of this repo is to test out Docker on Lubuntu. This project demonstrates a docker environment with:
*  **Maxscale** instance-a database load balancer (`maxscale`)
* **Master Databases** (MariaDB/MySQL), each initialized with a specific table.
  This setup is ideal for learning, testing, or developing database routing, high availability, or sharding solutions.

Note, I followed [https://docs.docker.com/compose/intro/features-uses/) in building the following demonstration.

## Setup


* I created **two database** (`master1`, `master2`) in my docker-compose.YML folder
* I created **one Maxscale** that routes connections to these databases in my docker-compose.YML folder
* Simple monitoring user and MaxScale configuration
* Ideal for learning replication, sharding, and load balancing with MaxScale

## Technologies used


Take a look at the [Installing Docker on Ubuntu Documentation](https://docs.docker.com/engine/install/ubuntu/).  Lubuntu is essentially a modified version of Ubuntu with less fancy graphics, so the same procedure for installing Docker on Ubuntu should work for Lubuntu.

Note the documentation states:

> To install Docker Engine, you need the 64-bit version of one of these Ubuntu versions:
>    Ubuntu Groovy 20.10
>    Ubuntu Focal 20.04 (LTS)
>    Ubuntu Bionic 18.04 (LTS)
>    Ubuntu Xenial 16.04 (LTS)

To check our underlying version of Ubuntu, we do:

```
~ : lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:        20.04
Codename:       focal
```

As we can see clearly above, Lubuntu "thinks," that it is Ubuntu 20.04, focal - so we should be good to go with Docker.

Sure enough, attempting to install Docker yields:

```
