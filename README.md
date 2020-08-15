# docker-davmail [https://github.com/johnhamelink/docker-davmail/actions?query=workflow%3ADocker](![Docker](https://github.com/johnhamelink/docker-davmail/workflows/Docker/badge.svg?branch=master))

A EWS proxy in docker. Run it like this:

```Bash
docker run --net=host \
           --name davmail \
           -e DAVMAIL_URL=<url> \
           -e DAVMAIL_SERVER_CERTIFICATE_HASH=<optional-certificate-hash>
           -e DAVMAIL_NTLM_DOMAIN=<optional-windows-domain>
           -d \
           gzm55/davmail
```

Accepted docker environment variables:

* DAVMAIL_MODE: connection mode auto, EWS or WebDav, default is EWS
* DAVMAIL_URL: server domain or ip
* DAVMAIL_SERVER_CERTIFICATE_HASH: optional, cirtificate hash, like 11:22:...
* DAVMAIL_NTLM_DOMAIN: optional, windows domain
* DAVMAIL_CONFIG_URL: a url for downloading a specific configuration, this can override all other options
* DAVMAIL_SSL_PASS: optional, set to the password of a PKCS12 SSL file
* DAVMAIL_BIND_ADDRESS: optional, set the URL that davmail should bind to
* DAVMAIL_NO_SECURE_CALDAV: optional, default: false, disable SSL for CalDAV
* DAVMAIL_NO_SECURE_IMAP: optional, default: false, disable SSL for IMAP
* DAVMAIL_NO_SECURE_LDAP: optional, default: false, disable SSL for LDAP
* DAVMAIL_NO_SECURE_POP: optional, default: false, disable SSL for POP
* DAVMAIL_NO_SECURE_SMTP: optional, default: false, disable SSL for SMTP

Listened ports:

* caldav port: 1080
* imap port:   993
* ldap port:   636
* pop3 port:   995
* smtp port:   587

Volume:

* "/etc/davmail/davmail.p12": if DAVMAIL_SSL_PASS is not empty, use this as the keystore file of type PKCS12
