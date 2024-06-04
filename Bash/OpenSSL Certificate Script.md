
```bash
#!/bin/bash
openssl req  -nodes -new -x509  \
    -keyout ./cert/server.key \
    -out ./cert/server.cert \
    -subj "/C=US/ST=State/L=City/O=company/OU=Com/CN=www.testserver.local"
```

This is a single command that will generate an SSL cert and associated private key. Since this is a self-signed cert for local use, the `subj` param doesn’t really matter and we can leave it as this generic value.

**Note:** This command assumes you have `openssl` installed on your machine, which is generally the case in unix (Mac/Linux) environments. If you’re on Windows, you may need to find another way to generate a self-signed cert!