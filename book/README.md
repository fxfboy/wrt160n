# Config WRT160N to corss GFW via DD-WRT

This is just a memo, it works on my router. Not sure it can help you!

## Prepare the router
My router is Linksys WRT160N v3 with 8MB flash.

## Install Shadowsocks
I'm using the Amazon EC2 as the server to install the Shadowsocks proxy server.
Any Linux server outside the GFW is okey.

## Install Redsocks2
Redsocks is a transparent proxy, the current Redsocks2 supports the Shadowsocks server
- [Redsocks2 Home page](https://github.com/semigodking/redsocks)
- [Redsocks2 Howto](https://github.com/semigodking/redsocks/wiki/REDSOCKS2%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)

## Install Dnscrypt
DNSCrypt is a protocol that authenticates communications between a DNS client and a DNS resolver. 
Download compiled binary dnscrypt-proxy for router from [here](http://files.lancethepants.com/)
