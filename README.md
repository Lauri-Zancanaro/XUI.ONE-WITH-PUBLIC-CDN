# XUI.ONE-WITH-PUBLIC-CDN

# How to Configure XUI.ONE with Public CDN Service Providers

XUI.ONE is a Popular OTT Middleware/Transcoding/Origin-Server

This Document will describe how to configure XUI.ONE Painel to PROXY LIVE STREAMING AND VOD CONTENT With a Public CDN Service Provider.

## Xui.One WEB Admin Interface Setup
### General Settings
#### Streaming
 - DISABLE "Encrypt HLS Segments"
 - ENABLE "Allow CDN / Forwarding"
 - API
 - ENABLE "Enable Cloudflare"
 - Security
 - ENABLE "Match Subnet of IP"
 - DISABLE "Logout On IP Change"
 - DISABLE "Restrict to Same IP"

 ## SERVERS
 - MANAGE SERVERS
 - EDIT MAIN SERVER
 - ADD IN "Domain Names" your-cdn-domain.com (Same domain configured in CDN Resource)

## Xui.One CLI/CONSOLE Setup

Edit file /home/XUI/bin/nginx/confcloudflare.conf

Add this lines:
```console
set_real_ip_from 0.0.0.0/0; ### use 0.0.0.0/0 or the prefixes from your CDN PROVIDER
set_real_ip_from 0::/0;


# EXMPLE WITH PREFIXES FROM CLOUDFLARE - IPv4
set_real_ip_from 173.245.48.0/20;
set_real_ip_from 103.21.244.0/22;
set_real_ip_from 103.22.200.0/22;
set_real_ip_from 103.31.4.0/22;
set_real_ip_from 141.101.64.0/18;
set_real_ip_from 108.162.192.0/18;
set_real_ip_from 190.93.240.0/20;
set_real_ip_from 188.114.96.0/20;
set_real_ip_from 197.234.240.0/22;
set_real_ip_from 198.41.128.0/17;
set_real_ip_from 162.158.0.0/15;
set_real_ip_from 104.16.0.0/13;
set_real_ip_from 104.24.0.0/14;
set_real_ip_from 172.64.0.0/13;
set_real_ip_from 131.0.72.0/22;

# EXMPLE WITH PREFIXES FROM CLOUDFLARE - IPv6
set_real_ip_from 2400:cb00::/32;
set_real_ip_from 2606:4700::/32;
set_real_ip_from 2803:f800::/32;
set_real_ip_from 2405:b500::/32;
set_real_ip_from 2405:8100::/32;
set_real_ip_from 2a06:98c0::/29;

```

