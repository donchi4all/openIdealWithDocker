# Quick start

## Requirement
[composer](https://getcomposer.org/)
Use composer 2
Note: use `$ composer -v` to get the version of composer.
If the verison is composer 1 run `$ composer self-update` or `$composer self-update --2`
[install Docker](https://docs.docker.com/)

## Steps

1. Run `$ composer Install` on openIdealWithDocker
2. `$ cd web` and run `$ composer install`
3. Go back to the root foleder by running `$ cd ../`
4. copy .env.example to .env ( for terminal `$ cp .env.example .env`) and set db information
   ```  PROJECT_NAME=openideal
        PROJECT_BASE_URL=openideal.docker.localhost
        DB_NAME=openideal

        MARIADB_TAG=10.7-3.19.0 // You can use any version of mariadb
        PHP_TAG=7.4-dev-4.36.0
        NGINX_VHOST_PRESET=drupal8
```
5. On the root folder Pulling/starting all containers by doing `$ make`
6. Enter the PHP container by doing `$ make shell`
7. `$ cd web`
8. `$ drush si -y --account-name admin --account-pass 123 --account-mail my_mail@example.com --site-name    "Openidea L" --db-url=mysql://drupal:drupal@mariadb/openideal idea`
9.  Set correct owner to sites/default/files: `$ chown -R wodby:www-data sites/default/files/`

Once the command has finishd executing, the `web` directory will hold all the necessary files to run OpenideaL. Proceed to installation of the site(s).

If you run into a `Fatal error: Allowed memory size of xxxxxxxx bytes exhausted`, try running the above command like this:

```
COMPOSER_MEMORY_LIMIT=-1 composer create-project linnovate/openideal-composer openideal
```

#### Troubleshooting

1. Make sure the composer has been installed on your local machine, otherwise you need to install
   the [composer](https://getcomposer.org/) before site installation
2. Make sure the docker has been installed on your local machine [docker](https://docs.docker.com/)
3. Please make sure you don't have the following files in the config directory before importing configs via Drush:

- core.extension.yml
- system.site.yml
