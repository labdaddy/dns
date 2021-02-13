## DNS STUFF
The below taken from a website called dnsmadeeasy. Article found [here.](https://social.dnsmadeeasy.com/blog/understanding-dns-forwarding/)
 What is DNS Forwarding
Clarifications

There’s occasionally some confusion between DNS forwarding and HTTP redirection or the use of CNAME records to designate DNS aliases.

    DNS forwarding exclusively refers to the process where specific DNS requests are forwarded to a designated DNS server for resolution.

It is not the solution for redirecting one domain to another, for which you would use an HTTP redirect. Nor is it useful for aliasing a subdomain to another domain: that’s the job of CNAME (Canonical Name) records.
What is DNS Forwarding?

DNS forwarding is the process by which particular sets of DNS queries are handled by a designated server, rather than being handled by the initial server contacted by the client. Usually, all DNS servers that handle address resolution within the network are configured to forward requests for addresses that are outside the network to a dedicated forwarder.

When deciding how to allocate DNS resources on a network it’s important to implement some separation between external and internal Domain Name Services. Having all DNS servers configured to handle both external and internal resolution can impact the performance and security of a network.
Terminology

The terminology around DNS forwarding can be a bit confusing because the forwarder has DNS queries forwarded to it by DNS servers that aren’t forwarders — try saying that five times quickly! The DNS forwarder should be thought of as the designated server to which a particular subset of queries (either for external addresses or specific internal addresses) are forwarded by other DNS servers within the network. It then sends (forwards) those requests for resolution to other DNS servers.
Why Use DNS Forwarding For External Addresses?

If no DNS server is designated as the forwarder to which external queries are routed, then all DNS servers within the network will handle external requests, which means that they will query external resolvers. This is undesirable for two main reasons:

    Internal DNS information can be exposed on the open Internet. It’s far better to have a strict separation between internal and external DNS. Exposing internal domains on the open Internet creates a potential security and privacy vulnerability.

    Without forwarding, all DNS servers will query external DNS resolvers if they don’t have the required addresses cached. This can result in excessive network traffic. By designating a DNS server as a forwarder, that server is responsible for all external DNS resolution and can build up a cache of external addresses, reducing the need to query recursive resolvers and cutting down on traffic. For smaller companies with limited available bandwidth, DNS forwarding can increase the efficiency of the network by both reducing bandwidth usage and improving the speed at which DNS requests are fulfilled.

DNS Forwarding For Internal Addresses

It’s also often useful to have a subset of internal addresses handled through DNS forwarding. For larger intranets with multiple domains and subdomains, it may be more efficient to have DNS requests for a subset of those domains handled by a dedicated server to which requests are forwarded with conditional DNS forwarding.
