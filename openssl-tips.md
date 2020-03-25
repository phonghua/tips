## Generate a CSR 
```openssl req -new -newkey rsa:2048 -nodes -keyout yourdomain.key -out yourdomain.csr```

## Encrypt a file using public key
```openssl rsautl -encrypt -inkey your-pubkey -pubin -in file.txt -out file-encrypted.txt```

## Decrypt a file using private key
```openssl rsautl -decrypt -inkey your-privatekey -in file-encrypted.txt -out file-descrypted.txt```

## Verify
```
vim sign.txt 
openssl dgst -sha256 -sign privatekey.key -out sign.txt.sha256 sign.txt
vim sign.txt.sha256
openssl dgst -sha256 -verify public-certificate.crt
vim sign.txt.sha256
openssl dgst -sha256 -verify <(openssl x509 -in public-certificate.crt -pubkey -noout) -signature sign.txt.sha256 sign.txt             
Verified OK
```
