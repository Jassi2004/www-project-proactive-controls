# C10: Stop Server Side Request Forgery

## Description

While Injection Attacks typically target the victim server itself, Server-Side Request Forgery (SSRF) attacks try to coerce the server to perform a request on behalf of the attacker. Why is this beneficial for the attacker? The outgoing request will be performed with the identity of the victim server and thus the attacker might execute operations with elevated operations.

## Threats

Examples of this contain:
- If an SSRF attack is possible on an server within the DMZ, an attacker might be able to access other servers within the DMZ without passing a perimeter firewall
- Many servers have local services running on localhost, often without any authentication/authorization as localhost. This can be abused by SSRF attacks.
- If SSO is used, SSRF can be used to extract tokens/tickets/hashes from servers.
- etc.

## Implementation

There multiple ways of preventing SSRF:
- Input validation
- If outgoing requests have to be made, check the target against an allow-list
- If using XML, configure parsers securely to prevent XEE
Be aware of [Unicode and other Character transformations](https://cheatsheetseries.owasp.org/assets/Server_Side_Request_Forgery_Prevention_Cheat_Sheet_Orange_Tsai_Talk.pdf) when performing input validation.

## Vulnerabilities Prevented

- [A10:2021 – Server-Side Request Forgery (SSRF)](https://owasp.org/Top10/A10_2021-Server-Side_Request_Forgery_%28SSRF%29/)

## References

- [Server-Side Request Forgery Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Server_Side_Request_Forgery_Prevention_Cheat_Sheet.html)
- [A New Era of SSRF - Exploiting URL Parser in Trending Programming Languages!](https://cheatsheetseries.owasp.org/assets/Server_Side_Request_Forgery_Prevention_Cheat_Sheet_Orange_Tsai_Talk.pdf)

## Tools

- [SSRFmap](https://github.com/swisskyrepo/SSRFmap)
