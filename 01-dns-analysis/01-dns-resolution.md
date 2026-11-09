# DNS Resolution Analysis

## Objective

Investigate how DNS resolution works by analyzing the domain `hunterxhunter.fandom.com`.

## Environment

- Operating System: Windows 11
- DNS tools: nslookup
- Packet analyzer: Wireshark
- DNS servers: Google DNS and Cloudflare DNS

## Methodology

The following tests were performed:

1. Resolved the domain using `nslookup`.
2. Queried the CNAME record.
3. Queried A and AAAA records.
4. Compared responses from Google DNS and Cloudflare DNS.
5. Captured and inspected DNS traffic using Wireshark.

## Results

### DNS Resolution

The domain resolved to:

- CNAME: `fandom.com.cdn.cloudflare.net`
- IPv4: `162.159.142.170`
- IPv4: `172.66.2.166`

### DNS Record Types

- A: Two IPv4 addresses were returned.
- AAAA: No IPv6 address was returned for the queried name.
- CNAME: The original domain points to `fandom.com.cdn.cloudflare.net`.

### DNS Server Comparison

Google DNS (`2001:4860:4860::8888`) and Cloudflare DNS (`1.1.1.1`) returned the same CNAME and IPv4 addresses.

A timeout message appeared during the Cloudflare DNS query, but the query eventually returned a response.

### Wireshark Analysis

A DNS query requesting the A record was captured.

The corresponding response contained:

- One CNAME record.
- Two A records.

This confirmed the DNS resolution chain observed in the terminal.

## Analysis

The investigation showed how a domain can use a CNAME record to point to another hostname, which then resolves to IPv4 addresses.

The DNS response observed in Wireshark matched the results obtained through nslookup.

## Conclusion

This experiment demonstrated the DNS resolution process, the relationship between CNAME and A records, and how DNS queries and responses can be inspected using Wireshark.
