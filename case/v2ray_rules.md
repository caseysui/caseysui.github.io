```
[
  {
    "outboundTag": "block",
    "domain": [
      "geosite:category-ads-all"
    ]
  },
  {
    "port": "",
    "inboundTag": [],
    "outboundTag": "direct",
    "ip": [
      "geoip:cn",
      "geoip:private"
    ],
    "domain": [
      "geosite:cn",
      "geosite:tld-cn",
      "geosite:private",
      "domain:windows.com",
      "domain:microsoft.com",
      "domain:jutal.com",
      "domain:pjoe.com.cn",
      "domain:caseysui.fun"
    ],
    "protocol": []
  },
  {
    "port": "0-65535",
    "inboundTag": [],
    "outboundTag": "proxy",
    "domain": [
      "geosite:geolocation-!cn"
    ]
  }
]
```