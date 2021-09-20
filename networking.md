# Networking Config

A basic overview/refresher of which services on are on which ports.

Inbound rules:

|Protocol|Port|Service|Sources|
|--------|----|-------|-------|
|TCP|22|SSH|all|
|TCP|6697|IRC|104.196.111.255/32, 104.199.121.36/32, 192.161.191.29/32|
|TCP|8444|Chia Node|all|

## DNS

Domain registrar for `strongco.de` is [iwantmyname](iwantmyname.com) but nameservers are forwarded to DO.

DNS record management is handled in [server-terraform](https://github.com/strong-code/server-terraform/blob/master/dns.tf) repo.
