# Config Split Debugging

This site is built on the [Composer template for Drupal projects](https://github.com/drupal-composer/drupal-project).
For getting started easily there is also a docker-compose file based on [docker4drupal](http://docs.docker4drupal.org/en/latest/).

## Installation

You can use your preferred php stack or you can use the docker-compose file.
Just do `docker-compose up -d` to start it.

If you have your own setting you need to override the database connections in `web/sites/default/settings.local.php` as
the default committed here are the ones used in docker for getting started easily.

Install all the composer dependencies.

`$ composer install`
or `$ docker-compose exec php composer install`

Then install the site from the provided configuration in your browser:

http://drupal.docker.localhost:8000/core/install.php?langcode=en&profile=config_installer

Or with drush:
`$ docker-compose exec php vendor/bin/drush --root=web si config_installer -y`

Now you should have a working site. The attempting to import the configuration should tell you that it is identical.
```
$ docker-compose exec php vendor/bin/drush --root=web cim

```


## Re-create the environment of your bug.

Starting from the installation instructions above create your site and configuration so that the bug shows itself.
Create new configuration, add modules by requiring them with composer etc.
Then export the configuration or dump the database.

Commit all the changes (including composer.lock and the database if needed).

Create a fork of this site and link to it in the bug report.

Document extra steps to take to re-create your bug.
