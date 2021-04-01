```
[
  {
    "outboundTag": "block",
    "domain": [
      "geosite:category-ads-all"
    ]
  },
  {
    "outboundTag": "direct",
    "ip": [
      "geoip:cn",
      "geoip:private"
    ],
    "domain": [
      "geosite:cn",
      "geosite:private",
      "geosite:tld-cn",
      "geosite:apple-cn",
      "geosite:google-cn",
      "domain:windows.com",
      "domain:microsoft.com",
      "domain:jutal.com",
      "domain:pjoe.com.cn"
    ]
  },
  {
    "port": "0-65535",
    "outboundTag": "proxy",
    "ip": [
      "geoip:us"
    ],
    "domain": [
      "geosite:geolocation-!cn"
    ]
  }
]
```
