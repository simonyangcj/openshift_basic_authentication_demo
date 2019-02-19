#  CREDENTIALS

Here you put all the sign crt in this folder

## Overview
* openssl genrsa -out ca.key 2048
* openssl req -new -x509 -key ca.key -out ca.crt
   *   Country Name (2 letter code) [AU]:cn
   *   State or Province Name (full name) [Some-State]:china
   *   Locality Name (eg, city) []:shanghai
   *   Organization Name (eg, company) [Internet Widgits Pty Ltd]:99cloud
   *   Organizational Unit Name (eg, section) []:99c
   *   Common Name (e.g. server FQDN or YOUR name) []:
   *   Email Address []:
* openssl genrsa -out admin.key 2048
* openssl req -new -key admin.key -out admin.csr -subj "/CN=localhost/O=localhost"
* openssl x509 -req -in admin.csr -CA ca.crt -CAkey ca.key -CAcreateserial -out admin.crt -days 365

