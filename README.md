# check-wordpress
CheckMK local check plugin for checking uavailable updates wordpress installations vie wp-cli.

Install wp cli (if not already on your system):
~~~
wget -O /usr/local/bin/wp https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
chmod +x /usr/local/bin/wp
wp --info
~~~

Install it into /usr/lib/check_mk_agent/local/ your Wordpress Host
```
interval=3600
mkdir -p /usr/lib/check_mk_agent/local/$interval
wget -O /usr/lib/check_mk_agent/local/$interval/check-wordpress https://raw.githubusercontent.com/bashclub/check-wordpress/main/check-wordpress
chmod +x /usr/lib/check_mk_agent/local/$interval/check-wordpress
/usr/lib/check_mk_agent/local/$interval/check-wordpress
```


After running once, the script will create the config file `/etc/check_mk/wordpress.conf` with default settings (JSON Format):
```
{
    "www.zmb.rocks": {
        "wp_user": "zmb",
        "wp_path": "/home/zmb/htdocs/www.zmb.rocks/",
        "wp_ignore_inactive_plugins": false,
        "wp_ignore_inactive_themes": false
    }
}

```

### Multiple instances example
```
{
    "www.zmb.rocks": {
        "wp_user": "zmb",
        "wp_path": "/home/zmb/htdocs/www.zmb.rocks/",
        "wp_ignore_inactive_plugins": false,
        "wp_ignore_inactive_themes": false
        }
    },
    "www.bashclub.org": {
        "wp_user": "bashclub",
        "wp_path": "/home/bashclub/htdocs/www.bashclub.org/",
        "wp_ignore_inactive_plugins": false,
        "wp_ignore_inactive_themes": false
        }
    }
}
```
