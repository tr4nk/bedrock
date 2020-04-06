# [Bedrock](https://roots.io/bedrock/) app template

## Requirements

* PHP >= 7.1
* Composer - [Install](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-osx)
* wp-cli - [Install](https://wp-cli.org/#installing)

## Installation

1. Create a new project:
    ```sh
    composer create-project roots/bedrock <project-name>
    ```
    Or clone this repo and run `composer install`.

2. Update environment variables in the `.env` file.
    * Database variables
        * `DB_NAME` - Database name
        * `DB_USER` - Database user
        * `DB_PASSWORD` - Database password
        * `DB_HOST` (optional) - Database host (default is `localhost`)
    * `WP_ENV` - Set to environment (`development`, `staging`, `production`)
    * `WP_HOME` - Full URL to WordPress home (https://web.test)
    * `WP_SITEURL` - Full URL to WordPress including subdirectory (https://web.test/wp)
    * `WP_DEBUG_LOG`
    * `AUTH_KEY`, `SECURE_AUTH_KEY`, `LOGGED_IN_KEY`, `NONCE_KEY`, `AUTH_SALT`, `SECURE_AUTH_SALT`, `LOGGED_IN_SALT`, `NONCE_SALT`
        * Generate with [wp-cli-dotenv-command](https://github.com/aaemnnosttv/wp-cli-dotenv-command)
            ```sh
            wp dotenv salts regenerate
            ```
        * Generate with [our WordPress salts generator](https://roots.io/salts.html)

4. Set the document root on your webserver to Bedrock's `web` folder.

0. Create database
    ```sh
    wp db create
    ```

0. Install WordPress in 5 seconds
    ```sh
    wp core install --url=web.test --title=Example --admin_user=trank --admin_password=secret --admin_email=khaitq77@gmail.com --skip-email
    ```

0. Remove all default wordpress themes (optional):
    ```sh
    rm -rf web/wp/wp-content/themes/*
    ```

    You can also deregister the wordpress default theme directory in `web/wp/wp-content/themes`:
    ```sh
    rm web/app/mu-plugins/register-theme-directory.php
    ```


0. Install a default theme. For example:
    ```sh
    # Use composer
    composer require wpackagist-theme/twentytwenty
    wp theme activate twentytwenty

    # Or use wp-cli
    wp theme install twentytwenty --activate
    ```
    If you use `composer` to install the theme, you should add the theme folder to `.gitignore` file.
    ```sh
    echo 'web/app/themes/twentytwenty/*' >> .gitignore
    ```

5. Access WordPress admin at `https://example.com/wp/wp-admin/`
