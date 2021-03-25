# picoCA

picoCA - a minimal certificate authority\
where simplicity is the main goal, not generality

 * Algorithm: ED25519
 * Default certificate lifetime: 100 years.
 * License: GPL 3.0 or later (https://www.gnu.org/licenses/gpl-3.0.en.html)
 * Author: Jo Totland

Creates certificates for client, server and CA in the current directory.
A CA will be automatically created when you create first certificate.

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

## Example:

```console
~$ mkdir ca; cd ca
~/ca$ picoCA create_server_cert server DNS:foo.com,DNS:bar.org
~/ca$ ls
ca.cert  ca.srl       server.certbundle  server.key+cert  server.pfx
ca.key   server.cert  server.key         server.p7b
~/ca$ picoCA create_client_cert client email:testing@example.org
~/ca$ ls
ca.cert  client.cert        client.key+cert  server.cert        server.key+cert
ca.key   client.certbundle  client.p7b       server.certbundle  server.p7b
ca.srl   client.key         client.pfx       server.key         server.pfx
~/ca$ cp server.* ca.cert /path/to/server/config
~/ca$ cp client.* ca.cert /path/to/client/config
```
