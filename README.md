# picoCA

picoCA - a minimal certificate authority\
where simplicity is the main goal, not generality

 * Default certificate lifetime: 100 years.
 * License: GPL 3.0 or later (https://www.gnu.org/licenses/gpl-3.0.en.html)
 * Author: Jo Totland

Creates certificates for client, server and CA in the current directory.
A CA will be automatically created when you create first certificate.
The openssl commands issued will be echoed to stderr

## Usage:
```
picoCA create_server_cert CN [SAN]
picoCA create_client_cert CN [SAN]
```
CN = is the common name of the certificate\
SAN = comma-separated list of subject alternate names (can be omitted)
```
picoCA inspect_key filename
picoCA inspect_cert filename
picoCA inspect_cert_bundle filename
```

```
