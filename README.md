##openvpn-install
OpenVPN [road warrior](http://en.wikipedia.org/wiki/Road_warrior_%28computing%29) installer for Debian, Ubuntu and CentOS.

This script will let you setup your own VPN server in no more than a minute, even if you haven't used OpenVPN before. It isn't bulletproof but has been designed to be as unobtrusive and universal as possible.

##Fork
This fork includes :
- No logs
- No comp-lzo [compression is a vector for oracle attacks, e.g. CRIME or BREACH](https://github.com/BetterCrypto/Applied-Crypto-Hardening/pull/91#issuecomment-75388575)
- Better encryption (see below)
- TLS 1.2 only
- AES-192-CBC by default and SHA-512 for HMAC (instead of BF-128-CBC and SHA1)
- Run server in unprivileged mode, reducing risks to the system
- TLS-auth to help [thwart DoS attacks](https://openvpn.net/index.php/open-source/documentation/howto.html#security) and provide a 2nd line of defense to the TLS channel.
- [Perfect forward secrecy](http://en.wikipedia.org/wiki/Forward_secrecy)
-[FDN's DNS Servers](http://www.fdn.fr/actions/dns/) (Option)
- Nearest [OpenNIC DNS Servers](https://www.opennicproject.org/) (Option)
- Support for either SNAT or MASQUERADE for forwarding
- Every feature of the [original script](https://github.com/Nyr/openvpn-install) (I check periodically to sync the latest commits from source)

## Variants

When you lauch the script you will be asked to choose a mode. Both will work the same way, but *slow* has higher encryption settings, so it may slow down your connection and take more time to install.

If you're just using your VPN at home, you may choose "fast". But if you're often using public Wi-Fi or traveling a lot, you choose use *Normal* or *slow*.

FYI, "fast" is still more secured than default OpenVPN settings.

### Slow (high encryption)
 Features :
- 8192 bits RSA private key
- 8192 bits Diffie-Hellman key
- 256 bits AES-GCM
- SHA-512 RSA certificate

### Normal (medium encryption)
Features :
- 4096 bits RSA private key
- 4096 bits Diffie-Hellman key
- 192 bits AES-GCM
- SHA-384 RSA certificate

### Fast (lower encryption, supports openvpn connect [ios/android] clients)
Features :
- 2048 bits RSA private key
- 2048 bits Diffie-Hellman key
- 128 bits AES-CBC
- SHA-128 RSA certificate

## Compatibility

The script is made to work on these OS :
- Debian 7
- Debian 8
- Ubuntu 12.04 LTS
- Ubuntu 14.04 LTS
- Ubuntu 15.10
- CentOS 6
- CentOS 7

Each one has been test by myself.

##Installation

Run the script and follow the assistant:

```
wget --no-check-certificate http://bit.ly/1ppnrmX -O openvpn-install.sh
chmod +x openvpn-install.sh
./openvpn-install.sh
```

Once it ends, you can run it again to add more users, remove some of them or even completely uninstall OpenVPN.


You can get a cheap VPS yearly at [VirtWire](https://my.virtwire.com/aff.php?aff=97).

## Licence

Based on the work of [Nyr](https://github.com/Nyr/openvpn-install)

[MIT Licence](https://raw.githubusercontent.com/Angristan/openvpn-install-nyr/master/LICENSE)
