# ansible-common-roles

Useful (somewhat) general-purpose ansible tasks.

General variables:

* deploy_type (should be set to 'vagrant' or 'ec2')

## common

Install common packages and set server's hostname.

Required Variables:

* hostname (default: "")
* extra_packages (default: [])

## django-base

Some base setup for django apps that `django` and `django-celery` depend on. Installs python (3 by default), creates project directories, creates the virtualenv, and sets up project code. Emits a `restart django-application` that can be used to restart app daemons such as uwsgi or celeryd.

Required Variables:

* project_name
* git_repositories - dictionary with keys: dir & repo (and optionally version)
* python_version (default: 3)

## django

A Django app running on nginx/uwsgi (inherits from django-base). It is assumed that if your deploy\_type is vagrant, your repo is included as a synced\_folder and does not need to be cloned (the "checkout project directories" task will be skipped).

Required Variables:

* project_name
* wsgi_module
* django_environment
* git_repositories - dictionary with keys: dir & repo (and optionally version)
* python_version (default: 3)

Optional Variables:

* processes (default: 4)
* port (default: 80)
* server_name (default: "")
* ssl_cert (default: "")
* ssl_key (default: "")
* nginx_locations (default: {})

## django-celery

Django and celery for distributed task queues (inherits from django-base).

Required Variables:

* project_name
* git_repositories - dictionary with keys: dir & repo (and optionally version)

Optional Variables:

* python_version (default: 3)
* concurrency (default 4)
* worker_nodes (default 3)
* celeryd\_max\_tasks\_per\_child  (default None)

## ebs

Create an EBS device

Variables:

* device_letter
* volume_size
* ebs_size

## mongo

Install MongoDB

## postgis

Postgres 9.3 w/ PostGIS 2.1

Variables:

* dbuser
* dbpassword
* dbname
* extensions (default: [])
