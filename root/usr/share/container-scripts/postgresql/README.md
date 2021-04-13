# PostgreSQL 12 SQL Database Server container image

This container image includes PostgreSQL 12 SQL database server for OpenShift and general usage.
Users can choose between RHEL, CentOS and Fedora based images,CentOS images are available on [Quay.io](https://quay.io/organization/centos7),

Usage
-----

```bash
$ sudo docker container run -dit --name postgresql --hostname postgresql -e POSTGRESQL_USER=<DB_USER> -e POSTGRESQL_PASSWORD=<DB_PASSWORD> -e POSTGRESQL_DATABASE=<DB_NAME> -p 5432:5432 leandromoreirajfa/postgres:12
```
# Environment variables

The image recognizes the following environment variables that you can set during
initialization by passing `-e VAR=VALUE` to the Docker run command.

**`POSTGRESQL_USER`**  
       User name for PostgreSQL account to be created

**`POSTGRESQL_PASSWORD`**  
       Password for the user account

**`POSTGRESQL_DATABASE`**  
       Database name

**`POSTGRESQL_ADMIN_PASSWORD`**  
       Password for the `postgres` admin account (optional)


Alternatively, the following options are related to migration scenario:

**`POSTGRESQL_MIGRATION_REMOTE_HOST`**  
       Hostname/IP to migrate from

**`POSTGRESQL_MIGRATION_ADMIN_PASSWORD`**  
       Password for the remote 'postgres' admin user

**`POSTGRESQL_MIGRATION_IGNORE_ERRORS (optional, default 'no')`**  
       Set to 'yes' to ignore sql import errors


The following environment variables influence the PostgreSQL configuration file. They are all optional.

**`POSTGRESQL_MAX_CONNECTIONS (default: 100)`**  
       The maximum number of client connections allowed

**`POSTGRESQL_MAX_PREPARED_TRANSACTIONS (default: 0)`**  
       Sets the maximum number of transactions that can be in the "prepared" state. If you are using prepared transactions, you will probably want this to be at least as large as max_connections

**`POSTGRESQL_SHARED_BUFFERS (default: 32M)`**  
       Sets how much memory is dedicated to PostgreSQL to use for caching data

**`POSTGRESQL_EFFECTIVE_CACHE_SIZE (default: 128M)`**  
       Set to an estimate of how much memory is available for disk caching by the operating system and within the database itself

**`/var/lib/pgsql/data`**  
       PostgreSQL database cluster directory