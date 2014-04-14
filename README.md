# ansible-common-roles

Useful (somewhat) general-purpose ansible tasks.

## common

Install common packages and set server's hostname.

Required Variables:

* hostname

Optional Variables:

* extra_packages (default: [])

## django

A Django app running on nginx/uwsgi.

Required Variables:

* project_name
* gitrepo
* settings
* wsgi_module

Optional Variables:

* processes (default: 4)
* port (default: 80)
* server_name (default: "")
* ssl_cert (default: "")
* ssl_key (default: "")
* nginx_locations (default: {})

## ebs

Create an EBS device

Required Variables:

* device_letter
* volume_size
* ebs_size

## postgis

Postgres 9.3 w/ PostGIS 2.1

Required Variables:

* dbuser
* dbpassword
* dbname
