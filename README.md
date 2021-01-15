# Start a Symfony project with Docker

> This repository is based on [Dunglas/symfony-docker](https://github.com/dunglas/symfony-docker) with some changes

- Caddy (Server)
- MySQL
- PhpMyAdmin

## Installation

***

### Retrieve repository

```shell
git clone  git@github.com:Damienbelingheri/Project_Symfony_Docker
```

### Go to the project directory

```shell
cd Project_Symfony_Docker
```

### Make this repository yours

### Configure your Database

```yaml
# docker-composer.yaml 
database:  
        MYSQL_DATABASE: name_of_your_database
        MYSQL_ROOT_PASSWORD: RootPa$$w0rd
        MYSQL_USER: user
        MYSQL_PASSWORD: userPa$$w0rd
        # Create a directory at the root of the project and push the content of /var/lib/mysql inside
      volumes:
      - .docker/data/db:/var/lib/mysql

php:
    environment:
      DATABASE_URL: mysql://${MYSQL_USER:-user}:${MYSQL_PASSWORD:-userPa$$w0rd}@database:3306/${MYSQL_DATABASE:-name_of_your_database}
```

### Run Docker

```shell
 docker-compose up -d
```
