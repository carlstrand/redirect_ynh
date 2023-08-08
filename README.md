<!--
N.B.: This README was automatically generated by https://github.com/YunoHost/apps/tree/master/tools/README-generator
It shall NOT be edited by hand.
-->

# Redirect for YunoHost

[![Integration level](https://dash.yunohost.org/integration/redirect.svg)](https://dash.yunohost.org/appci/app/redirect) ![Working status](https://ci-apps.yunohost.org/ci/badges/redirect.status.svg) ![Maintenance status](https://ci-apps.yunohost.org/ci/badges/redirect.maintain.svg)

[![Install Redirect with YunoHost](https://install-app.yunohost.org/install-with-yunohost.svg)](https://install-app.yunohost.org/?app=redirect)

*[Lire ce readme en français.](./README_fr.md)*

> *This package allows you to install Redirect quickly and simply on a YunoHost server.
If you don't have YunoHost, please consult [the guide](https://yunohost.org/#/install) to learn how to install it.*

## Overview

This application allows to integrate a custom tile in YunoHost's user portal. Typical use cases include:
- **visible 301/302 redirect** : having a "virtual" app tile that's just a redirection to another url or external website
- **invisible redirect / reverse-proxy** : creating an app tile for a local app listening on a specific port, or a Docker container, or an app hosted on another machine

In technical terms: this app only adds a NGINX configuration snippet with either `redirect` or `proxy_pass` rule, and a YunoHost tile + appropriate SSOwat configuration.


**Shipped version:** 1.0.2~ynh2
## Disclaimers / important information

## Redirect type

### Visible redirect

The client will be redirected to another url or external website

- `your-domain.com -> another-domain.net`
- `your-domain.com/foo -> another-domain.net/bar`

### Invisible redirect (a.k.a "reverse-proxy")

Visitor's address bar will remain the same. Typically used to integrate into YunoHost a manually-installed app into the portal.
    
- `you-domain.com/foo -> http://172.0.0.1:8080/app`

**IMPORTANT:** you may have to further tweak the `redirect.conf` in the nginx configuration, depending on your needs!

**IMPORTANT:** Many apps do not support being redirected to a different path due to relative links! This means that some apps being hosted for example on http://127.0.0.1:5050/app/ MUST be redirected to http://domain.tld/app/ and NOT http://domain.tld/someotherapp/. For example : an Odoo Docker container runs on http://127.0.0.1:8069/. You will not be able to redirect it to http://domain.tld/odoo/ ! You have to redirect it to the root, so for example http://odoo.domain.tld/

## Documentation and resources

* Upstream app code repository: <https://github.com/YunoHost-Apps/redirect_ynh>
* YunoHost documentation for this app: <https://yunohost.org/app_redirect>
* Report a bug: <https://github.com/YunoHost-Apps/redirect_ynh/issues>

## Developer info

Please send your pull request to the [testing branch](https://github.com/YunoHost-Apps/redirect_ynh/tree/testing).

To try the testing branch, please proceed like that.

``` bash
sudo yunohost app install https://github.com/YunoHost-Apps/redirect_ynh/tree/testing --debug
or
sudo yunohost app upgrade redirect -u https://github.com/YunoHost-Apps/redirect_ynh/tree/testing --debug
```

**More info regarding app packaging:** <https://yunohost.org/packaging_apps>
