![logo](https://products.containerize.com/devops/compose/header_image.png)

# Final-docker-compose-YML on Lubuntu
Objective
The purpose of this repo is to test out Docker on Lubuntu. This project demonstrates a docker environment with:
*  **Maxscale** instance-a database load balancer (`maxscale`)
* **Master Databases** (MariaDB/MySQL), each initialized with a specific table.
  This setup is ideal for learning, testing, or developing database routing, high availability, or sharding solutions.

Note, I followed [https://docs.docker.com/compose/intro/features-uses/) in building the following demonstration.

## ⚙️Setup


* I created **two database** (`master1`, `master2`) in my docker-compose.YML folder
* I created **one Maxscale** that routes connections to these databases in my docker-compose.YML folder
* Simple monitoring user and MaxScale configuration
* Ideal for learning replication, sharding, and load balancing with MaxScale

## 📦 Technologies used

- [MariaDB 11.4](https://mariadb.com/docs/maxscale/other-maxscale-versions/mariadb-maxscale-25/maxscale-25-tutorials/mariadb-maxscale-25-simple-sharding-with-two-servers)
- [MariaDB MaxScale](https://mariadb.com/products/technology/maxscale/)
- Docker & Docker Compose

```
  ## 📁 Project Structure

Final-docker-compose-YML/
├── docker-compose.yml # Docker services for MariaDB and MaxScale
├── maxscale.cnf # MaxScale routing and monitoring config
└── README.md # Project overview and setup instructions
```

## 🚀 Setup Instructions

### 1. Clone this Repository

```bash
git clone https://github.com/My_USERNAME/Final-docker-compose-YML.git
cd Final-docker-compose-YML
```
## Start the Containers

```
bash
docker compose up -d
```

This brings up:

`master1` and `master2` MariaDB instances with `root` password `root123`

A MaxScale instance exposing ports:

`4000`: SQL client access

`8989`: MaxScale admin interface
🔐 Step 3: Create MaxScale Monitoring User in Both Masters
On master1:

`bash
docker exec -it master1 mysql -uroot -proot123`

> sql

CREATE USER 'maxscale'@'%' IDENTIFIED BY 'maxscale123';
GRANT ALL PRIVILEGES ON *.* TO 'maxscale'@'%' WITH GRANT OPTION;
FLUSH PRIVILEGES;
EXIT;

On master2:

`bash
docker exec -it master2 mysql -uroot -proot123`

Repeat the same SQL commands.
