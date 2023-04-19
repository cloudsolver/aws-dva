Server Name Indication (SNI) is supported by [[CloudFront]], [[ALB]] and [[NLB]] 
The newer protocol solves the problem of loading multiple SSL certificates onto one web server - to server multiple websites. In the past, one webserver would have to host multiple certs. Now, [[ELB]] 
It's a newer protocol and requires the client to indicate the hostname of the target server in the initial SSL handshake.

### Deep Dive
SSL certificates are loaded onto Application Load Balancers (ALBs) to enable them to use Server Name Indication (SNI) and provide secure connections to multiple domains hosted on the same server.

When a client initiates a connection to a server using HTTPS, the server sends its SSL certificate to the client to prove its identity. The SSL certificate contains the domain name for which the certificate is issued. In the case of an ALB, the SSL certificate includes the domain names for all the websites hosted on the server.

With SNI, the client includes the hostname in the initial TLS handshake request, and the server responds with the appropriate SSL certificate for that hostname. This allows the server to use a single IP address to host multiple domains, each with its own SSL certificate.

To enable SNI on an ALB, you must first upload the SSL certificates for each domain hosted on the server to the ALB. You can do this using the AWS Certificate Manager service, which allows you to request and manage SSL certificates for your domains. Once you have uploaded the SSL certificates, you can configure the ALB to use them for secure connections.

When a client connects to the ALB using HTTPS and provides the hostname in the request, the ALB uses SNI to select the appropriate SSL certificate for that hostname and establishes a secure connection with the client.