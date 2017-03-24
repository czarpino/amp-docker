# AMP Docker

Dockerized version of the good old AMP stack to get you up and running in no time. There are two PHP containers to choose from: PHP5.6 and PHP7.1. Both use the same database to make testing easy for applications currently on PHP5.6 planning a migration to PHP7.1.

## What's in the box

- PHP5.6
- PHP7.1
- Apache Httpd v2.2 (with mod_php)
- MySQL 5.7

## Getting started

1. Clone this repository

        git clone git@github.com:czarpino/amp-docker.git
        
2. Create a symlink named `src` from the PHP project into the `amp-docker` directory

        ln -s /Path/to/PHP/project amp-docker/src

3. Copy default configuration files into the PHP docker directory

        cp amp-docker/defaults/* amp-docker/php56
        cp amp-docker/defaults/* amp-docker/php71
        
4. Bring up the AMP5.6 or AMP7.1 stack. NOTE: Only one should be running at a time since both use the same port 80.

        docker-compose up php56
        # OR
        docker-compose up php71
        
5. Checkout your website at `127.0.0.1`

# Initializing a database

SQL files inside the `mysql` directory will be executed on docker-compose up (with some caveats). This is particularly useful to create an initial database and/or tables.
