Installing Maestro
==================

Pre-requisites
--------------
CentOS 6.4+
Root access
PostgreSQL database user


Installed
---------
Install script deps:
* Expect

Maestro deps:
* Maestro YUM Repositories
* Maestro Server (bundled w/ LuCEE)
* Maestro Agent
* PostgreSQL Server
* MongoDB Server
* ActiveMQ
* Perl libs
  * Getopt::Long::Descriptive
  * REST::Client
  * LWP
  * JSON::XS


Running
-------

* Untar/Unzip the maestro-installer package
* Copy maestro-account.properties.example to maestro-account.properties and enter your Maestro Account credentials
* Run ./maestro-installer and follow the instructions


PostgreSQL
----------

The basic PostgreSQL settings for Maestro to connect to PostgreSQL are listed below.

/var/lib/pgsql/data/postgresql.conf:

    listen_addresses = 'localhost'    # commend out this line to enable TCP/IP connections

/var/lib/pgsql/data/pg_hba.conf:

    host    all         all         127.0.0.1/32          md5    # enable connections to localhost
    host    all         all         ::1/128               md5    # enable connections to localhost via IPV6


NOTE: You will be prompted to create a Maestro database user and databases, which match the settings in
/var/local/maestro/conf/maestro_lucee.json

