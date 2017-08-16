# AusNimbus Component for MariaDB [![Build Status](https://travis-ci.org/ausnimbus/mariadb-component.svg?branch=master)](https://travis-ci.org/ausnimbus/mariadb-component) [![Docker Repository on Quay](https://quay.io/repository/ausnimbus/mariadb-component/status "Docker Repository on Quay")](https://quay.io/repository/ausnimbus/mariadb-component)

[![MariaDB](https://user-images.githubusercontent.com/2239920/27766273-63d98028-5f0e-11e7-97cf-bccf24e50086.jpg)](https://www.ausnimbus.com.au/)

The [AusNimbus](https://www.ausnimbus.com.au/) component for [MariaDB](https://www.ausnimbus.com.au/instant-apps/mariadb/).

This document describes the behaviour and environment configuration when running MariaDB on AusNimbus.

## Table of Contents

- [Runtime Environments](#runtime-environments)
- [Environment Configuration](#environment-configuration)
- [Advanced](#advanced)
  - [Auto Tuning](#auto-tuning)

## Runtime Environments

AusNimbus supports the latest stable release for MariaDB.

The currently supported versions are `10.1` and `10.2`

## Environment Configuration

The following environment variables are available for you to configure your MariaDB environment:

NAME                       | Description
---------------------------|-------------
MYSQL_ROOT_PASSWORD        | Specifies the password that will be set for the MariaDB root superuser account. (REQUIRED)
MYSQL_DATABASE             | Specify the name of a database to be created on startup. If a user/password was supplied then that user will be granted superuser access (corresponding to GRANT ALL) to this database.
MYSQL_USER, MYSQL_PASSWORD |   Specify the user that will be granted superuser permissions for the database specified by the `MYSQL_DATABASE` variable. Both variables are required for a user to be created.

## Advanced

### Auto Tuning

The MariaDB component is automatically tuned based on your container size. The following variables map to their corresponding `my.cnf`:

NAME                            | Default
--------------------------------|-------------
MYSQL_MAX_ALLOWED_PACKET        | 200M
MYSQL_TABLE_OPEN_CACHE          | 2000
MYSQL_LOWER_CASE_TABLE_NAMES    | 0
MYSQL_FT_MIN_WORD_LEN           | 4
MYSQL_FT_MAX_WORD_LEN           | 20
MYSQL_INNODB_BUFFER_POOL_SIZE   | autotuned
MYSQL_INNODB_LOG_FILE_SIZE      | autotuned
MYSQL_INNODB_LOG_BUFFER_SIZE    | autotuned
MYSQL_THREAD_COCURRENCY         | autotuned
MYSQL_MAX_CONNECTIONS           | autotuned

### Galera Cluster

The `POD_NAMESPACE` environment variable is required to be set for the `peer-finder` eg:

```yaml
- name: POD_NAMESPACE
  valueFrom:
    fieldRef:
      apiVersion: v1
      fieldPath: metadata.namespace
```
