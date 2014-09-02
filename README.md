# LAMP stack fig/docker environment

This project is designed to allow a developer to quickly get a LAMP stack setup for both local development and production on a single server.

The project uses the [fig](http://orchardup.github.io/fig/) to orchestrate docker containers so that PHP works with PHP-FPM/nginx and MySQL database backend.

## Prerequisites

- [Docker](http://docs.docker.com/installation/#installation)
- [Fig](http://orchardup.github.io/fig/install.html)

## Quick Start

Use `fig up -d` build and start the project. (If you modify anything in the containers folder, then you should run `fig build`)

The LAMP site should be available at (http://localhost/).

## Running and stoping containers

If you want to top the containers then run `fig stop`.  If you want to start it up again, use `fig up -d`.

## Developing

Simply change the contents of the `www` directory to see changes to the website.

### Helper scripts

Three helper scripts have can be used to access a PHP CLI (command line interface), MySQL CLI or bash terminal to explore the PHP container.

The `phpcli` script can be used to enter a PHP interactive terminal.

The `mysqlcli` script can be used to enter a MySQL interactive terminal.  It is here that you could add your tables or explore the sites database.  The database credentials are as follows:

HOST: db_1
USER: root
DATABASE: db

There is not a password for the root user.

The `explore` script runs bash on the PHP container.

NOTE: These scripts run in a copy of the PHP container.  It isn't specifically the container that is running the site.  However, the PHP container does connect to the actual running MySQL database.
