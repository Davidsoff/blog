---
title: "Intro to DNS"
date: 2019-11-11T12:55:23+01:00
summary: A short introduction into the innerworkings of DNS
---
layout: true

class: center, middle

---

# Intro to DNS

By: David Soff (@SoffDavid)

---

# DNS

---

# **D**omain **N**ame **S**ystem

---

# Basically the phonebook of the internet

---

# How does it work?

--

1. A browser or device called the *DNS client* issues a *DNS Request*. For example: *google.com*
--

2. The request is received by the *DNS resolver*. The resolver starts to look for a DNS server that holds the ip address for the domain
--

3. The resolver starts at the internets *Root DNS server* to find the **T**op **L**evel **D**omain* server.
--

4. The resolver then goes to the server responsible for the *domain*. If there are *subdomains* managed by a different server, the resolver wil go to those servers.
--

5. Once the resolver gets to the *authoritative DNS server* for the specific *domain*, that DNS server will return de requested data to the resolver. The request is now resolved.
--

6. The client can now connect to the correct server with the returned IP address.

---

# Now some terms:

- **DNS client**: Any device making a DNS request
- **DNS resolver**: The program or server the DNS client is sending the DNS request to.
- **Root DNS server**: These servers know where all the DNS servers for the Top Level Domains are.
- **Authoritative DNS server**: These servers are the one and only source where you can get the address information for a specific domain.
- **DNS request**: A request for the DNS information associated with a particular domain

---

# Other interesting things

- DNS resolvers may cache the responses they get for a request.
- A response contains a **T**ime-**T**o-**L**ive field which is meant to be an indicator of how long the DNS record should be kept in the cache.
- A resolver does not have to respect the TTL field of a DNS response. for example: Some mobile phone plans cache responses for at least 2 hours. Lower values for the TTL are not respected.

---

# Thank you

---

# Sources and more information:
- https://ns1.com/resources/dns-protocol
- https://umbrella.cisco.com/blog/2014/07/16/difference-authoritative-recursive-dns-nameservers/
- https://www.cloudflare.com/learning/dns/what-is-dns/