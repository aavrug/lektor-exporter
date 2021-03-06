# WordPress to Lektor Exporter

One-click WordPress plugin that converts all posts, pages, taxonomies, metadata, to contents.lr Markdown files in proper folders which can be dropped into Lektor.

Most of the code of this plugin has been derived from the excellent plugin [Jekyll Exporter](https://github.com/benbalter/wordpress-to-jekyll-exporter) by [Ben Balter](https://github.com/benbalter) - Thanks a lot for writing free code, Ben!

## A Note

Many shared hosts may use PHP 5.2 by default. **WordPress to Lektor Export requires PHP 5.3 or greater.**

If you get an error message that looks like `unexpected T_STRING` or `expecting T_CONSTANT_ENCAPSED_STRING`, you need to update your PHP version. In a shared hosting environment, you should be able to change the version of PHP used by simply toggling the setting in the host's control panel.

PHP 5.2 lost support from the PHP project itself more than *five* years ago. You'll need to be running at least PHP 5.3 which adds namespace support (the reason it's breaking), but I'd recommend at least 5.5 (or the latest your host supports) as it's the oldest supported version: https://en.wikipedia.org/wiki/PHP#Release_history

## Features


* Converts all posts, and pages, from WordPress for use in Lektor
* Export what your users see, not what the database stores (runs post content through `the_content` filter prior to export, allowing third-party plugins to modify the output)
* Converts all `post_content` to Markdown Extra (using Markdownify)
* Outputs Lektor compatible file in exports/ folder within the plugin folder
* No settings. Just a single click.

## Usage

1. Place plugin in `/wp-content/plugins/` folder
2. Activate plugin in WordPress dashboard
3. Ensure that the exports folder within the plugin is writeable by webserver
4. Select `Export to Lektor` from the `Tools` menu
5. Check the exports folder for the converted files

## Command-line Usage

If you're having trouble with your web server timing out before the export is complete, or if you just like terminal better, you may enjoy the command-line tool.

It works just like the plugin.

```
php lektor-export-cli.php
```

If using this method, you must run first `cd` into the wordpress-to-lektor-exporter directory.

Alternatively, if you have [WP-CLI](http://wp-cli.org) installed, you can run:

```
wp lektor-export
```

The WP-CLI version will provide greater compatibility for alternate WordPress environments, such as when `wp-content` isn't in the usual location.

## Custom post types

To export custom post types, you'll need to add a filter to do the following:

```php
add_filter( 'lektor_export_post_types', array('posts', 'pages', 'you-custom-post-type') );
```
This feature is still in development.

## Changelog

* Initial release

## License

The project is licensed under the GPLv3 or later
