# Composer Boilerplate for Drupal Contenta
This boilerplate uses the [drupal-composer]

## Features

- Drupal 9 version: **^9.0**
- Contenta version **8.x-3.x**
- Development mode is already configured. Just Uncomment:
 `if (file_exists($app_root . '/' . $site_path . '/settings.local.php')) {
  include $app_root . '/' . $site_path . '/settings.local.php';
}` in `settings.php` file.
- Core and Contrib module dependencies are managed by Composer.

## Getting Started
These instructions will get you a copy of the project up and running on your local machine for development

### # Requirements
- PHP version >= 8.0
- Composer version >= 2.0

### # Installation using Lando
```
NOTE: before running the installation, please make sure to follow the requirements above.
```

1. Go to `/Development` folder. Create `websites` folder.
2. Remove `.git` under `/drupal-contenta/` folder.
3. Git clone the `drupal-contenta`under `/Development/websites`.
4. Go to `/drupal-contenta/` folder.
5. Edit `lando.yml` then change the name `drupal-contenta` to your prefer name or base on your root directory name.
6. Run `lando start`
7. Copy the `.env.lando.example` and rename it to `.env`. Edit `.env`.
8. Run `lando info` to get the credentials for `MYSQL_DATABASE`, `MYSQL_USER`, `MYSQL_PASSWORD`, `MYSQL_HOSTNAME`, `MYSQL_PORT`.
9. Set your `MYSQL_DATABASE`, `MYSQL_USER`, `MYSQL_PASSWORD`. In `MYSQL_HOSTNAME`, leave it as `database` value and for `MYSQL_PORT`, leave it as `3306`.
7. Copy the `.env.local.example` and rename it to `.env.local`. Edit `.env.local`.
9. Set your `SITE_MAIL`, `ACCOUNT_MAIL`, `SITE_NAME`, `ACCOUNT_NAME`,`ACCOUNT_PASS`.
10. Run `lando composer install` in the `/drupal-contenta/` directory.
11. Run `lando composer run-script install:with-mysql` in the `/drupal-contenta/` directory.
12. To run `drush-cli`, you can use `lando drush`.
13. Last is to run `lando rebuild -y` in your terminal. Make sure you are in the root directory

### # Drupal Installation
```
NOTE: before running the installation, please make sure to follow the requirements above.
```

1. Clone the project repo 
2. Delete the `.git` folder inside the root directory
3. Copy the `.env.example` and rename it to `.env`. Edit `.env`.
4. Set your `MYSQL_DATABASE`, `MYSQL_USER`, `MYSQL_PASSWORD`. In `MYSQL_HOSTNAME`, leave it as `localhost` value and for `MYSQL_PORT`, leave it as `3306`.
5. Copy the `.env.local.example` and rename it to `.env.local`. Edit `.env.local`.
6. Set your `SITE_MAIL`, `ACCOUNT_MAIL`, `SITE_NAME`, `ACCOUNT_NAME`,`ACCOUNT_PASS`.
7. Run `composer install` in the root directory.
8. Run `composer run-script install:with-mysql` in the root directory.
9. Uncomment
`if (file_exists($app_root . '/' . $site_path . '/settings.local.php')) {  include $app_root . '/' . $site_path . ' settingslocal.php'; }` in `settings.php` to enable development mode
10. Clear cache, Run updb, Run cron

### # I get issue with the caching like (Render, Page & Dynamic Page Cache)
Go to the `settings.local.php`. Comment these line of code:

- `$settings['cache']['bins']['render'] = 'cache.backend.null';`
- `$settings['cache']['bins']['page'] = 'cache.backend.null';`
- `$settings['cache']['bins']['dynamic_page_cache'] = 'cache.backend.null';`

### # Going to live the Website
Make sure to change the permission of the folder.
List of folders and files to change:

- root/private - 755
- root/private/backup_migrate - 755
- root/web/sites/default - 555
- root/web/sites/default/files - 755
- root/web/sites/default/settings.php - 444


Developed by <a href="https://halcyonwebdesign.com.ph/" target="_blank">Halcyon Web Design</a> Drupal Team