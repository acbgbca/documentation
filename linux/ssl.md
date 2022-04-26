# SSL

From <https://github.com/xcad2k/cheat-sheets/blob/main/misc/ssl-certs.md> and <https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/>

## Generate Certificate Authority Certificate

Generate a private key: ```openssl genrsa -aes256 -out ca.key 4096```

Generate a root certificate: ```openssl req -new -x509 -sha256 -days 1825 -key ca.key -out ca.pem```

## Generate Signed Certificate

Generate private key: ```openssl genrsa -out cert-key.pem 4096```

Generate CSR: ```openssl req -new -sha256 -subj "/CN=microserver.local" -key cert-key.pem -out cert.csr```

Create an extfile (extfile.cnf) with the additional information:

```
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName = @alt_names

[alt_names]
DNS.1 = server.local
DNS.2 = *.local
```
Create the signed certificate: ```openssl x509 -req -sha256 -days 365 -in cert.csr -CA ca.pem -CAkey ca.key -out cert.pem -extfile extfile.cnf -CAcreateserial```

## View the Signed Certificate

Run: ```openssl x509 -in cert.pem -text```

## Add Root Certificate

### Linux

Copy CA certificate (ca.pem) into /usr/local/share/ca-certificates/ca.crt.

Then run: ```sudo update-ca-certificates```
