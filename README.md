# docker-php-apache

Apache + php 7.1.1 + MySQL + PhpMyAdmin

## Installation

1. Create a `.env` from the `.env.dist` file

    ```
    cp .env.dist .env
    ```

2. Change environment variable 

    ```
    # Application's path 
    WORKSPACE_APP_PATH=./app
    
    # MySQL
    MYSQL_ROOT_PASSWORD=root
    MYSQL_DATABASE=my_db
    MYSQL_USER=root
    MYSQL_PASSWORD=root
    ```

3. Adapt the `vhost.conf` file in `.ldocker/apache` at you convenience.

4. Build containers by typing : 

    ```
    $ docker-compose build
    $ docker-compose up -d
    ```

5. Update you system host file (/etc/hosts) by adding this line
    ```
    X.X.X.X      my_app.dev    
    ```

    Where **X.X.X.X** corresponds to container IP address and **my_app.dev** to server name.
    
    To know the container IP, first get the container ID :
    ``` 
    $ docker ps
    ``` 
    (First column is for container ID)
    ```
    $ docker inspect <container ID>
    ```
    At the bottom,under "NetworkSettings", you can find "IPAddress"

## Commands

```
# bash commands
$ docker-compose exec php-apache bash

# MySQL commands
$ docker-compose exec db mysql -uroot -p"root"

# Delete all containers
$ docker rm $(docker ps -aq)

# Delete all images
$ docker rmi $(docker images -q)

# Use composer 
$ docker-compose exec php-apache composer ...

#Use php command
$ docker-compose exec php-apache ...
```


