# AMP Docker

Dockerized version of the good old AMP stack to get you up and running in no time.

## What's in the box

- PHP5.6
- Apache Httpd v2.2 (with mod_php)
- MySQL 5.7

## Getting started

1. Clone this repository

        git clone git@github.com:czarpino/amp-docker.git
        
2. Create a symlink named `src` from the PHP project into the `amp-docker` directory

        ln -s /Path/to/PHP/project amp-docker/src

3. Copy default configuration files into the PHP docker directory

        cp amp-docker/defaults/* amp-docker/php56
        
4. Bring up the AMP stack containers!

        docker-compose up

# Initializing a database

SQL files inside the `mysql` directory will be executed on docker-compose up (with some caveats). This is particularly useful to create an initial database and/or tables.
