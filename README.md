# AusNimbus Component for MariaDB *WIP* [![Build Status](https://travis-ci.org/ausnimbus/mariadb-component.svg?branch=master)](https://travis-ci.org/ausnimbus/mariadb-component) [![Docker Repository on Quay](https://quay.io/repository/ausnimbus/mariadb-component/status "Docker Repository on Quay")](https://quay.io/repository/ausnimbus/mariadb-component)

[![MariaDB](https://user-images.githubusercontent.com/2239920/27714621-613923b8-5d75-11e7-87fc-2cbd6fdc0db8.jpg)](https://www.ausnimbus.com.au/)

The [AusNimbus](https://www.ausnimbus.com.au/) component for [MariaDB](https://www.ausnimbus.com.au/instant-apps/mariadb/). 

## Environment Variables

The following environment variables are available to configure your MariaDB instance:

- **MYSQL_ROOT_PASSWORD**
  This variable is mandatory and specifies the password that will be set for the MariaDB root superuser account.

- **MYSQL_DATABASE**
  This variable is optional and allows you to specify the name of a database to be created on image startup. If a user/password was supplied (see below) then that user will be granted superuser access (corresponding to GRANT ALL) to this database.

- **MYSQL_USER, MYSQL_PASSWORD**
  This user will be granted superuser permissions for the database specified by the `MYSQL_DATABASE` variable. Both variables are required for a user to be created.

## Versions

The versions currently supported are:

- 10.1
