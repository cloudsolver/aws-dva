## Summary
Domain Name System (DNS) is a hierarchical naming structure that translates host names to IP addresses.

## DNS Details
URL resolution happens right to left.
https://www.resume.rohitsood.com 
`www.resume.rohitsood.com.` < `.` is the root domain.
 `.com` is the Top-Level Domain.
`.rohitsood.com` is the Second-Level Domain .

### Browser Route
_This is what happens when you want to visit a website?_
![DNS Resolver|600](https://cf-assets.www.cloudflare.com/slt3lc6tev37/1NzaAqpEFGjqTZPAS02oNv/bf7b3f305d9c35bde5c5b93a519ba6d5/what_is_a_dns_server_dns_lookup.png)
1. User types in the URL into the browser.
	1. It connects to a local DNS server or a DNS resolver IP.
	2. Local DNS Server is managed or assigned by ISP.
	4. DNS Settings on Local Machine ![DNS | 250](dns-settings.png)
2. Root Name Server
	1. The DNS Resolver Queries the Root Name Server `.`
	2. The Root Name Server responds with the IP Address of the TLD `.com` NS
3. TLD NS
	1. The resolver then makes a call to the TLD NS IP Address with a request for `.rohitsood.com`
	2. The TLD NS returns the address for the domain's NS.
4. SLD Name Server
	1. DNS resolver requests the NS for IP address.
5. Browser gets IP Address
	1. DNS resolver gets the IP Address to the browser.
6. Sends request to IP Address
	1. Browser uses the IP address to make a call.

## Domain Registrar
- Registers Second Level Domain
### DNS Records
* Each record contains domain / sub-domain name.
[Route 53](Route%2053.md)
### Zone File
### Hosted Zones
- Container for records that define how to route traffic to a domain and sub-domains.
- *Public Hosted Zones* contain records for public domain names.
- _Private Hosted Zone_ contains records for private domain names (e.g. intranet names). $0.50 per month.
- 
### Name Server
- Authoritative or Non-Authoritative
- `dig` and `nslookup` can provide information on the domain name to IP mapping.
#### Top Level Domain (TLD)
- com is the top level domain
#### Second Level Domain (SLD)
- rohitsood.com
- resume is sub-domain
#### URI, URC, URL and URN

All URLs, URCs and URNs are types of URIs.

![Venn| 300](https://i.stack.imgur.com/FbaKm.png)
## References

1. https://stackoverflow.com/questions/176264/what-is-the-difference-between-a-uri-a-url-and-a-urn
1. https://aws.amazon.com/blogs/networking-and-content-delivery/solving-dns-zone-apex-challenges-with-third-party-dns-providers-using-aws/
