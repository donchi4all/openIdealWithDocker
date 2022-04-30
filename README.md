# OpenideaL - ideas and innovation management system

![OpenideaL logo](https://www.openidealapp.com/wp-content/uploads/2018/02/logo_OpenideaL.png)

## Overview

**OpenideaL** (OI) is the leading open source ideas and innovation management system.

Out of the box it provides an ideation community where citizens, employees, clients or any other group of stake holders can create, discuss, rate and promote ideas.

Since 2010 OpenideaL is in use by various organizations including multi-national and top-500  companies, governments, cities, universities and NGOs.

OpenideaL includes tools for the website managers which allow them to identify *successful* ideas (those ideas which have a better chance to be relaized), and to pass them along to professional teams within the organization. Community members are rewarded with points for their activity in the system (creating ideas, participating in discussions etc.)

OI is based on Drupal, and therefore it is modular, and allows growth and adaptation to the organization’s specific needs. These adaptations may include a unique design, polls and surveys, interfacing with external applications or adapting the interface to a range of devices ans apis.

## Prerequisites:
Since OpenideaL relies on [Drupal](https://www.drupal.org/) and is subject to its system requirements, it is recommended ensuring that you have satisfied the [Drupal System Requirements](https://www.drupal.org/docs/system-requirements) before moving forward.


## Requirement
1. Use composer 2 [composer](https://getcomposer.org/)
  Note: use `$ composer -v` to get the version of composer.
  If the verison is composer 1 run `$ composer self-update` or `$composer self-update --2`
2. [install Docker](https://docs.docker.com/)

## Steps

1. Run `$ composer Install` on openIdealWithDocker
2. `$ cd web` and run `$ composer install`
3. Go back to the root foleder by running `$ cd ../`
4. copy .env.example to .env ( for terminal `$ cp .env.example .env`) and set db information
   ``  PROJECT_NAME=openideal
        PROJECT_BASE_URL=openideal.docker.localhost
        DB_NAME=openideal

        MARIADB_TAG=10.7-3.19.0 // You can use any version of mariadb
        PHP_TAG=7.4-dev-4.36.0
        NGINX_VHOST_PRESET=drupal8``
5. On the root folder Pulling/starting all containers by doing `$ make`
6. Enter the PHP container by doing `$ make shell`
7. `$ cd web`
8. `$ drush si -y --account-name admin --account-pass 123 --account-mail my_mail@example.com --site-name    "Openidea L" --db-url=mysql://drupal:drupal@mariadb/openideal idea`
9.  Set correct owner to sites/default/files: `$ chown -R wodby:www-data sites/default/files/`

Once the command has finishd executing, the `web` directory will hold all the necessary files to run OpenideaL. Proceed to installation of the site(s).

If you run into a `Fatal error: Allowed memory size of xxxxxxxx bytes exhausted`, try running the above command like this:
`
COMPOSER_MEMORY_LIMIT=-1 composer install
`

#### Troubleshooting

1. Make sure the composer has been installed on your local machine, otherwise you need to install
   the [composer](https://getcomposer.org/) before site installation
2. Make sure the docker has been installed on your local machine [docker](https://docs.docker.com/)
3. Please make sure you don't have the following files in the config directory before importing configs via Drush:

- core.extension.yml
- system.site.yml
