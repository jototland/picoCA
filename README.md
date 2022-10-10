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

## Example:

```console
~$ mkdir ca; cd ca
~/ca$ picoCA create_server_cert server DNS:foo.com,DNS:bar.org
...
~/ca$ ls
picoCA.crt         picoCA.srl         server.key             server.p7b
picoCA.key         server.certbundle  server.key+cert        server.pfx
picoCA.server.ext  server.crt         server.key+certbundle
~/ca$ picoCA create_client_cert client email:testing@example.org
...
~/ca$ ls
client.certbundle      picoCA.client.ext  server.key
client.crt             picoCA.crt         server.key+cert
client.key             picoCA.key         server.key+certbundle
client.key+cert        picoCA.server.ext  server.p7b
client.key+certbundle  picoCA.srl         server.pfx
client.p7b             server.certbundle
client.pfx             server.crt
~/ca$ cp server.* ca.crt /path/to/server/config
~/ca$ cp client.* ca.crt /path/to/client/config
```
