## Let’s Generate SSL Certificates

Before we proceed further let’s create a directory to store the certificates inside our app folder.  

```
mkdir cert
```

Now move to the cert directory using cd command:  

```
cd cert
```

To generate the SSL Certificate we need to follow these steps as shown below:

- Generate a Private Key
- Create a CSR ( certificate signing request) using the private key.
- Generate the SSL certification from CSR

## [](https://dev.to/devland/how-to-generate-and-use-an-ssl-certificate-in-nodejs-2996#generate-a-private-key)Generate a Private Key

To generate a private key we need to install [OpenSSL](https://www.openssl.org/), a full-featured toolkit for the Transport Layer Security (TLS) and Secure Sockets Layer (SSL) protocols, on our local machine. These articles can help you install it. [Windows](https://tecadmin.net/install-openssl-on-windows/) - [Ubuntu](https://linuxpip.org/install-openssl-linux/).

After the installation, we need to run this command as shown below to generate the private key:  

```
openssl genrsa -out key.pem
```

Once we ran the above command it will generate the private key and save it in _key.pem_ file inside cert directory and gives this type of message in the terminal.  

```
Generating RSA private key, 2048 bit long modulus
...+++
.................+++
e is 65537 (0x10001)
```

## [](https://dev.to/devland/how-to-generate-and-use-an-ssl-certificate-in-nodejs-2996#create-a-csr-certificate-signing-request)Create a CSR (Certificate Signing Request)

Since we are our own certificate authority, we need to use CSR to generate our certificate. To do so we need to run the below command.  

```
openssl req -new -key key.pem -out csr.pem
```

Once we ran this command it will ask a few questions as shown below:

[![Image questions](https://res.cloudinary.com/practicaldev/image/fetch/s--ei5E0hhd--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/8oab1sg8gtlkeetljj55.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--ei5E0hhd--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/8oab1sg8gtlkeetljj55.png)

You can skip any question by simply pressing enter else if you want to provide the details you can provide them, it’s totally up to you.

Once you are done with these questions it will generate the CSR in _csr.pem_ file inside _cert_ folder.

## [](https://dev.to/devland/how-to-generate-and-use-an-ssl-certificate-in-nodejs-2996#generate-the-ssl-certificate)Generate the SSL Certificate

Now for the final steps, we need to use the _key.pem_ and _csr.pem_ files to generate our SSL certificate.

let’s run the below command to generate it.  

```
openssl x509 -req -days 365 -in csr.pem -signkey key.pem -out cert.pem
```

_Note: We are using x509 because it is the standard defining the format of the public-key certificate. We set the validity of the certificate as 365 days._

After running the above command it will save the certificate in the _cert.pem_ file inside cert folder. Now you can remove the _csr.pem_ file or you can keep it.

## [](https://dev.to/devland/how-to-generate-and-use-an-ssl-certificate-in-nodejs-2996#integration-of-the-ssl-certificate-in-express)Integration of the SSL Certificate in Express

Now let’s use these certificates inside our app using the file system (fs) and path module. To do so, we need to edit a few lines in our app as mentioned below.

Earlier we had created a constant variable option. Now we will update that part of the code by adding the path of the generated certificates inside it as shown below.

Before:  

```
const options = {
key:'',
cert:''
}
```

After:  

```
const options = {
key:fs.readFileSync(path.join(__dirname,'./cert/key.pem')),
cert:fs.readFileSync(path.join(__dirname,'./cert/cert.pem'))
}
```

Once it’s done save it and run the server with:  

```
npm start
```

You can check if HTTPS is working or not by just accessing it from this URL:  
`https://localhost:1337`

[![Image browser](https://res.cloudinary.com/practicaldev/image/fetch/s--BQOa-tpT--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ct73p170i8z14en9n7rk.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--BQOa-tpT--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ct73p170i8z14en9n7rk.png)

## [](https://dev.to/devland/how-to-generate-and-use-an-ssl-certificate-in-nodejs-2996#conclusion)Conclusion

You might see ‘Not Secure’ in your browser though we have a valid certificate, it is just because we have generated the certificate and it is not generated by some known certificate authorities, so, your browser doesn’t trust you as a valid certificate authority.  
But we should typically use this process for development purposes and for production we should be using a certificate that is generated by a certificate authority.