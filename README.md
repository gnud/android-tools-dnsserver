# Purpose

You don't have a router capable of editing static DNS entries, e.g:
dev.product.com to 192.168.0.123

This solution with DNSMasq powered by a Docker container.


# Disable Built-in DNSMasq on ubuntu

Do this step only if nothing is resolved on your computer's browser.

Make sure:

/etc/resolv.conf


```
nameserver 1.1.1.1
```

You can also use: 8.8.8.8, 8.8.4.4 and many more free dns servers to the outside world.


has only that

edit /etc/systemd/resolved.conf

```
DNSStubListener=no
```

Restart systemd-resolved


```
sudo systemctl restart systemd-resolved.service
```


# Usage

```docker-compose up -d``` or ```docker-compose up``` to debug


# Monitor

Web interface for DNSMasq

http://localhost:8080/


# Config

Either open the web interface and append this line:
address=/dev.product.com/192.168.0.123


# Testing

dig dev.product.com

dig @8.8.8.8 dev.product.com

dig 127.0.0.1 dev.product.com # using the DNSMasq container
