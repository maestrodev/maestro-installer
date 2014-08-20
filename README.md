Installing Maestro
==================

Pre-requisites
--------------
* CentOS 6.5+
* Root access
* PostgreSQL database user

Running
-------
Maestro master server releases:

    \bash < <( curl -sL https://raw.githubusercontent.com/maestrodev/maestro-installer/master/maestro-install )

Maestro agent service:

    \bash -s agent maestro_master_hostname < <( curl -sL https://raw.githubusercontent.com/maestrodev/maestro-installer/master/maestro-install )

Maestro master server snapshots:

    \bash -s snapshots < <( curl -sL https://raw.githubusercontent.com/maestrodev/maestro-installer/master/maestro-install )

NOTES:
* You will need to provide your Maestro Account credentials.
* The \ must be removed from the command line above when pasting into a terminal.
* If any temporary failures occur, the installer can safely be run multiple times to resume progress.
 
System Requirements
-------------------
**Maestro Head - Minimum Requirements:**
* VM or Physical Machine
  * 1.7GB+ RAM
  * 1 core (2+ recommended)
  * 1.5GB DISK (plus working space for projects, output logging, etc.)
* CentOS 6.5
  * root access
  * base image + updates
* Network access:
  * Agent connections (inbound ports: 8080, 61613)
  * yum.maestrodev.com (outbound ports: 80, 443)
  * repo.maestrodev.com (outbound ports: 80, 443)
  * CentOS and EPEL yum repos as needed

**Maestro Agent - Linux - Minimum Requirements:**
* VM or Physical Machine
  * 512GB+ RAM (dependent on target workload to be performed)
  * 1GB DISK (dependent on target workload to be performed)
* CentOS 6.5
  * Java 1.6
* Network access:
  * Maestro Head (outbound ports: 8080, 61613)

Dependencies
------------
The following packages / components are installed if not present during installation.

Install script:
* Expect
* Perl libs
  * JSON::XS

Maestro:
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

YUM Repos:
* EPEL
* Maestro YUM Repositories

PostgreSQL
----------

The basic PostgreSQL settings for Maestro to connect to PostgreSQL are listed below.

`/var/lib/pgsql/data/postgresql.conf`:

    listen_addresses = 'localhost'    # comment out this line to enable TCP/IP connections

`/var/lib/pgsql/data/pg_hba.conf`:

    host    all         all         127.0.0.1/32          md5    # enable connections to localhost
    host    all         all         ::1/128               md5    # enable connections to localhost via IPV6


NOTE: You will be prompted to create a Maestro database user and databases, which match the settings in
`/var/local/maestro/conf/maestro_lucee.json`

