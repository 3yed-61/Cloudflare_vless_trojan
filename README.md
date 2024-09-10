# Cloudflare Workers/Pages Proxy Script
### This project only supports local deployment and does not rely on third-party external links like subscription converters or node transformers, so there's no need to worry about external access to node subscriptions.

--------------------------------
## Script Features:
### Designed for beginners! The default nodes are Cloudflare (CF) official IPs, eliminating the need to frequently update subscriptions to get optimized client IPs.
#### Workers Method: Supports vless+ws+tls, trojan+ws+tls, vless+ws, and trojan+ws proxy nodes.
#### Pages Method: Supports vless+ws+tls and trojan+ws+tls proxy nodes.
#### CF Vless/Trojan single nodes support path customization with three types of proxy IPs (IPv4, IPv6, domain name format).
#### Supports single node links, aggregated universal node subscriptions, sing-box node subscriptions, and clash node subscriptions.

--------------------------------

## 1: Customizable Content for CF Vless Nodes

#### Method 1 (Recommended): Modify the _worker.js file in the Vless_workers_pages folder.

1. **UUID** must be customized (line 7).
2. If you cannot access CF-related websites or the ChatGPT web version, the ProxyIP may have expired. You can replace the ProxyIP (line 9).
3. Customizable preferred IPs for subscription nodes (lines 13-27) and ports (lines 30-44); IPs and ports must match in numbering.
4. The disguise page is empty by default, showing the local IP information interface. You can customize this (line 10), but to avoid risks, it is recommended to leave it blank.

#### Method 2: You can also use variable settings in the CF-workers/pages interface.

Note: Variable settings will override local modifications.

| Function           | Variable Name  | Value Requirements             | Default Value                      |
|--------------------|----------------|---------------------------------|------------------------------------|
| 1. Required UUID   | uuid           | Must comply with UUID format    | Default UUID: 77a571fb-4fd2-4b37-8596-1b7d9728bb5c |
| 2. Proxy IP for CF | proxyip        | IPv4 address, domain, [IPv6 address] | ProxyIP domain (line 9)            |
| 3. Preferred IPs   | ip1 to ip13    | CF official IPs, CF proxy IPs, CF preferred domains | CF official domains from various regions |
| 4. Ports for IPs   | pt1 to pt13    | 13 standard CF ports, any ports for proxy IPs | 13 standard CF ports                |

---------------------------------

## 2: Customizable Content for CF Trojan Nodes

#### Method 1 (Recommended): Modify the _worker.js file in the Trojan_workers_pages folder.

1. **Password** must be customized (line 4).
2. If you cannot access CF-related websites or the ChatGPT web version, the ProxyIP may have expired. You can replace the ProxyIP (line 5).
3. Customizable preferred IPs for subscription nodes (lines 9-23) and ports (lines 26-40); IPs and ports must match in numbering.
4. The disguise page is empty by default, showing the local IP information interface. You can customize this (line 6), but to avoid risks, it is recommended to leave it blank.

#### Method 2: You can also use variable settings in the CF-workers/pages interface.

Note: Variable settings will override local modifications. Every time you update variables, you need to re-upload the original pages file.

| Function           | Variable Name  | Value Requirements             | Default Value                      |
|--------------------|----------------|---------------------------------|------------------------------------|
| 1. Required Password | pswd         | Any string                     | Default Password: trojan           |
| 2. Proxy IP for CF  | proxyip        | IPv4 address, domain, [IPv6 address] | ProxyIP domain (line 5)            |
| 3. Preferred IPs    | ip1 to ip13    | CF official IPs, CF proxy IPs, CF preferred domains | CF official domains from various regions |
| 4. Ports for IPs    | pt1 to pt13    | 13 standard CF ports, any ports for proxy IPs | 13 standard CF ports                |

---------------------------------
## 3: CF Vless/Trojan Single Node Path Customization for ProxyIP

Supports three methods: IPv4, IPv6 (requires brackets), and domain name formats.

You can modify the path directly in the client: `/pyip=IPv4 address` or `/pyip=[IPv6 address]` or `/pyip=domain`.

Note: This only affects the single node being configured and does not impact other nodes or subscription nodes.

---------------------------------

## 4: Viewing Configuration Information and Sharing Links

CF Vless: Enter the following in the browser address bar: `https://workers-domain` or `pages-domain` or `custom-domain/custom-uuid`.

CF Trojan: Enter the following in the browser address bar: `https://workers-domain` or `pages-domain` or `custom-domain/custom-password`.

Note: When using a custom domain, the configuration information and sharing links under the original workers or pages domain remain usable.

---------------------------------

## 5: Preferred IP Application

If you don't need top speed every day or selecting a specific country, you can use the default CF official domains from various regions (all IP landing locations are in the USA).

For lazy users, we recommend the following easily remembered CF official IPs (all IP landing locations are in the USA, supporting 13 standard ports):

- 104.16.0.0
- 104.17.0.0
- 104.18.0.0
- 104.19.0.0
- 104.20.0.0
- 104.21.0.0
- 104.22.0.0
- 104.24.0.0
- 104.25.0.0
- 104.26.0.0
- 104.27.0.0
- 172.66.0.0
- 172.67.0.0
- 162.159.0.0
- 2606:4700:: (requires IPv6 environment)

You can modify the configuration variables to use shared IPs or domains, or select your own locally preferred ones. For more information, refer to the video tutorials.

Note: When using load balancing or automatic selection across multiple CF nodes in the client, it is recommended to have all nodes in the same country/region to avoid IP bouncing between countries.

---------------------------------
## 6: No Need for SOCKS5! Easily Create ProxyIP with Reality Protocol and Use Any Port from the 80/443 Series

#### Recommended: Use a pure IPv6 VPS close to China with low cost and high traffic!
#### Note: Avoid using IPv4 when possible! IPv4 is likely to be scanned by third parties and added to public or paid proxy IP databases.

Options for ProxyIP and Reverse Proxy IP:

1. **Reality 1**: Use for preferred client IP, where the CF node’s IP landing location for non-CF websites matches the VPS region, and the IP landing location for CF websites is determined by ProxyIP.
2. **Reality 2**: Use for ProxyIP, where the CF node’s IP landing location for CF websites matches the VPS region, and the IP landing location for non-CF websites is determined by the preferred client IP.
3. **Reality 3**: Use for both preferred client IP and ProxyIP, where the IP landing locations for both CF and non-CF websites match the VPS region (only supports TLS nodes on port 443).
4. **Reality 4**: Use WARP for full IPv4+IPv6 stack on VPS, fixing the IP landing location for both CF and non-CF websites to WARP-enabled regions.

Recommended scripts for ProxyIP and Reverse Proxy IP setup: [x-ui-yg script](https://github.com/yonggekkk/x-ui-yg), [sing-box-yg script](https://github.com/yonggekkk/sing-box_hysteria2_tuic_argo_reality).

For more information, refer to the [video tutorials](https://youtu.be/QOnMVULADko).

---------------------------------
## 7: Recommended Clients

#### Benefits of Enabling Fragmentation: Bypass domain-blocked TLS interruptions, allowing workers or other blocked domains to support TLS nodes.
#### Tip: Custom or pages domains that are not blocked by TLS interruptions do not need fragmentation to support TLS nodes.

Supported platforms (click the name for the download link):

1. **Android**: [v2rayNG](https://github.com/2dust/v2rayNG/tags), [Nekobox](https://github.com/maskedeken/NekoBoxForAndroid/tags), [Karing](https://github.com/KaringX/karing/tags), v2box
2. **Windows**: [v2rayN](https://github.com/2dust/v2rayN/tags), [Hiddify](https://github.com/hiddify/hiddify-next/tags), [Karing](https://github.com/KaringX/karing/tags)
3. **iOS**: Karing, Shadowrocket, Streisand, v2box
4. **OpenWRT**: [homeproxy](https://github.com/kiddin9/openwrt-packages)

Note: Clients on other platforms without fragmentation support cannot use workers’ six 443-series TLS nodes.

---------------------------------
### For more information, visit the [Yongge Blog](https://ygkkk.blogspot.com/2023/07/cfworkers-vless.html)

### Video Tutorials:
- [CF Workers Vless Setup Tutorial 1](https://youtu.be/9V9CQxmfwoA)
- [CF Workers Vless Setup Tutorial 2](https://youtu.be/McdRoLZeTqg)
- [CF Workers Trojan Setup Tutorial 3](https://youtu.be/lmhhL8M1k0I)
- [CF Vless/Trojan Node Tutorial 4](https://youtu.be/NaLd-orwFUE)

---------------------------------
### Preferred domain name, preferred official IP + reverse IP one-click script (run using termux or ish in the local network environment):

#### CF-CDN prefers public domain name scripts for Apple, Android, and tablets:
```bash
curl -sSL https://gitlab.com/rwkgyg/CFwarp/raw/main/point/CFcdnym.sh -o CFcdnym.sh && chmod +x CFcdnym.sh && bash CFcdnym.sh

```
------------------------------------------------------------------------
### CF-optimized official IP + anti-generation IP two-in-one script, dedicated to Apple Android phones and tablets:
```
curl -sSL https://gitlab.com/rwkgyg/CFwarp/raw/main/point/cfip.sh -o cfip.sh && chmod +x cfip.sh && bash cfip.sh
```

-------------------------------------------------------------

### Communication platform: [Yongge blog address](https://ygkkk.blogspot.com), [Yongge YouTube channel](https://www.youtube.com/@ygkkk), [Yongge TG Telegram group](https://t.me/+jZHc6-A-1QQ5ZGVl), [Yongge TG Telegram channel](https://t.me/+DkC9ZZUgEFQzMTZl)

-------------------------------------------------------------
Don’t forget to give it a star! 🌟
[![Stargazers over time](https://starchart.cc/yonggekkk/Cloudflare-workers-pages-vless.svg)](https://starchart.cc/yonggekkk/Cloudflare-workers-pages-vless)
------------------------------------------------------------------------
### Code Sources：[ca110us](https://github.com/ca110us/epeius)、[emn178](https://github.com/emn178/js-sha256/blob/master/src/sha256.js)、[3Kmfi6HP](https://github.com/3Kmfi6HP/EDtunnel)、[badafans](https://github.com/badafans/Cloudflare-IP-SpeedTest)、[XIU2](https://github.com/XIU2/CloudflareSpeedTest)

### Disclaimer: All code comes from the Github community and has been integrated through ChatGPT
