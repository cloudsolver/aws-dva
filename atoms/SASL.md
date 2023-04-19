## Summary
Decouple internet protocols from specific authentication mechanisms [Simple Authentication and Security Layer](https://tools.ietf.org/html/rfc4422) (SASL) #secure 

## SASL Detail
In an application, we may use SMTP to send emails and use LDAP to access directory services. But each of these protocols may support another authentication mechanism, like Digest-MD5 or Kerberos.

What if there was a way for protocols to swap authentication mechanisms more declaratively? This is exactly where SASL comes into the picture. Protocols supporting SASL can invariably support any of the SASL mechanisms.

Hence, **applications can negotiate a suitable mechanism** and adopt that for authentication and secure communication.
![](https://www.baeldung.com/wp-content/uploads/2019/09/SASL-Exchange.jpg)
## References

	1.https://www.baeldung.com/java-sasl