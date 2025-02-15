# Hass.io Core Add-on: MariaDB

MariaDB database for Home Assistant.

![Supports aarch64 Architecture][aarch64-shield] ![Supports amd64 Architecture][amd64-shield] ![Supports armhf Architecture][armhf-shield] ![Supports armv7 Architecture][armv7-shield] ![Supports i386 Architecture][i386-shield]

## About

You can use this add-on to install MariaDB, which is an open-source (GPLv2 licensed) database.  MariaDB can be used as the database backend for Home Assistant. For more information, please see [MariaDB][mariadb]

## Installation

The installation of this add-on is straightforward and easy to do.

1. Navigate in your Home Assistant frontend to **Hass.io** -> **Add-on Store**.
1. Find the "MariaDB" add-on and click it.
1. Click on the "INSTALL" button.

## How to use

1. Set the `logins` -> `password` field to something strong and unique.
1. Start the add-on.
1. Check the add-on log output to see the result.
1. Add `recorder` component to your Home Assistnat configuration.

## Add-on Configuration

The MariaDB server add-on can be tweaked to your likings. This section
describes each of the add-on configuration options.

Example add-on configuration:

```json
{
  "databases": [
    "homeassistant"
  ],
  "logins": [
    {
      "username": "hass",
      "host": "%",
      "password": null
    }
  ],
  "rights": [
    {
      "username": "hass",
      "host": "%",
      "database": "homeassistant",
      "grant": "ALL PRIVILEGES ON"
    }
  ]
}
```

### Option: `databases` (required)

Database name, e.g., `homeassistant`

### Option: `logins` (required)

This section defines a create user definition in MariaDB. [Create User][createuser] documentation.

### Option: `logins` -> `username` (required)

Database user login, e.g., `hass`. [User Name][username] documentation.

### Option: `logins` -> `host` (required)

Hostname allowed to connect to database. [Host Name][hostname] documentation.

### Option: `logins` -> `password` (required)

Password for user login. This should be strong and unique.

### Option: `rights` (required)

This section grant privileges to users in MariaDB. [Grant][grant] documentation.

### Option: `rights` -> `username` (required)

This should be the same user name defined in `logins` -> `username`.

### Option: `rights` -> `host` (required)

This should be the same hostname defined in `logins` -> `host`.

### Option: `rights` -> `database` (required)

This should be the same database defined in `databases`.

### Option: `rights` -> `grant` (required)

This is the grant statement giving your user access to the databse.

## Home Assistant Configuration

MariaDB will be used by the `recorder` and `history` components within Home Assistant.  For more information about setting this up, see the [MariaDB][mariadb-hass] documentation for Home Assistant. 

Example Home Assistant configuration:

```json
recorder:
  db_url: mysql://hass:password@core-mariadb/homeassistant?charset=utf8
```

## Support

Got questions?

You have several options to get them answered:

- The [Home Assistant Discord Chat Server][discord].
- The Home Assistant [Community Forum][forum].
- Join the [Reddit subreddit][reddit] in [/r/homeassistant][reddit]

In case you've found an bug, please [open an issue on our GitHub][issue].

[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[armhf-shield]: https://img.shields.io/badge/armhf-yes-green.svg
[armv7-shield]: https://img.shields.io/badge/armv7-yes-green.svg
[mariadb]: https://mariadb.com
[createuser]: https://mariadb.com/kb/en/library/create-user
[username]: https://mariadb.com/kb/en/library/create-user/#user-name-component
[hostname]: https://mariadb.com/kb/en/library/create-user/#host-name-component
[grant]: https://mariadb.com/kb/en/library/grant
[mariadb-hass]: https://www.home-assistant.io/addons/mariadb
[discord]: https://discord.gg/c5DvZ4e
[forum]: https://community.home-assistant.io
[i386-shield]: https://img.shields.io/badge/i386-yes-green.svg
[issue]: https://github.com/home-assistant/hassio-addons/issues
[reddit]: https://reddit.com/r/homeassistant
[repository]: https://github.com/hassio-addons/repository
