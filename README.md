# plushu-app-nginx-servers

This plugin creates a configuration specifying Nginx servers for an app, on
domains specified by plugins like [plushu/plushu-domains][] or
[plushu/plushu-app-name-domain][]. It hooks these domains up to the upstream
location specified by a configuration from a plugin like
[plushu/plushu-app-nginx-upstream-docker][].

Assuming app Nginx configurations have been integrated into the main Nginx
configuration, ie. as part of the installation of the
[plushu/plushu-nginx-apps][] plugin (which also manages configurations in the
event of an app fork/rename/destroy), this configuration will proxy requests
to apps by listening on the host interface via the
[plushu/plushu-nginx-container][] (or the legacy host-based
[plushu/plushu-nginx][]) plugin.

[plushu/plushu-domains]: https://github.com/plushu/plushu-domains
[plushu/plushu-app-name-domain]: https://github.com/plushu/plushu-app-name-domain
[plushu/plushu-app-nginx-upstream-docker]: https://github.com/plushu/plushu-app-nginx-upstream-docker
[plushu/plushu-nginx-apps]: https://github.com/plushu/plushu-nginx-apps
[plushu/plushu-nginx-container]: https://github.com/plushu/plushu-nginx-container
[plushu/plushu-nginx]: https://github.com/plushu/plushu-nginx

## SSL / TLS

This plugin automatically sets domains to be HTTPS-only (redirecting on plain
HTTP requests) when there is an SSL certificate and key available for that
domain. It checks certificates in the "ssl" directories within $PLUSHU_ROOT
(and/or a subdiectory with the app's name within that directory). At some point
in the future, it's planned to have a "certs" plugin for managing these
certificates; for now, they just have to be added to the appropriate directory
via other means (such as logging in as root and/or uploading them via sftp).
