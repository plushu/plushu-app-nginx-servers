# plushu-nginx-app-vhosts

This plugin connects apps to the host interface via Nginx virtual hosts. It
requires [plushu/plushu-nginx][] to be installed and it makes apps available
on domains specified by plugins like [plushu/plushu-domains][] or
[app-name-domain][plushu/plushu-app-name-domain].

[plushu/plushu-nginx]: https://github.com/plushu/plushu-nginx
[plushu/plushu-domains]: https://github.com/plushu/plushu-domains
[plushu/plushu-app-name-domain]: https://github.com/plushu/plushu-app-name-domain

## SSL / TLS

This plugin automatically sets domains to be HTTPS-only (redirecting on plain
HTTP requests) when there is an SSL certificate and key available for that
domain. It checks certificates in the "ssl" directories within $PLUSHU_ROOT and
the app's directory (under $PLUSHU_APPS_DIR). At some point in the future,
it's planned to have a "certs" plugin for managing these certificates; for now,
they just have to be added to the appropriate directory via other means (such
as logging in as root and/or uploading them via sftp).
