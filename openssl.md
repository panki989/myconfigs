## openssl cheatsheet

### Verify SSL certificate with its key:
```
openssl x509 -in new.crt -pubkey -noout -outform pem | openssl md5
openssl pkey -in test.private-key -pubout -outform pem | openssl md5
```

### Convert p7b format to crt
```
openssl pkcs7 -print_certs -in test.p7b -out new.crt
```

### Convert pem/crt to p12 format
```
openssl x509 -in new.crt -out test.pem -outform PEM
openssl pkcs12 -export -out test_file.p12 -inkey test.private-key -in test.pem
```

### Validate the end date for crt
```
openssl x509 -enddate -noout -in new.crt
```

### Check crt file details 
```
openssl x509 -in new.crt -text -noout
```

### Extract crt/certificate chain from the domain to configure in keytool
```
openssl s_client -crlf -connect google.com:443 -servername google.com
```

### To generate the CSR and key
```
openssl req -out /tmp/www.test.com.csr -newkey rsa:2048 -nodes -keyout /tmp/www.test.com_signing.key \
-subj "/C=IN/ST=Maharashtra/L=Mumbai/O=Test Pvt Ltd/OU=TEST-OU/CN=www.test.com"
```
