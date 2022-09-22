```
#代理规则
[
  {
    "outboundTag": "block",
    "domain": [
      "geosite:category-ads-all"
    ],
    "enabled": true
  },
  {
    "inboundTag": [],
    "outboundTag": "proxy",
    "domain": [
      "geosite:github",
      "geosite:google",
      "geosite:telegram",
      "geosite:tiktok"
    ],
    "enabled": true
  },
  {
    "inboundTag": [],
    "outboundTag": "direct",
    "domain": [
      "geosite:microsoft",
      "geosite:apple",
      "geosite:apple-cn",
      "geosite:category-games@cn",
      "geosite:cn",
      "geosite:private",
      "geosite:win-extra",
      "geosite:win-spy",
      "geosite:win-update"
    ],
    "enabled": true
  },
  {
    "inboundTag": [],
    "outboundTag": "direct",
    "ip": [
      "geoip:cn",
      "geoip:private"
    ],
    "enabled": true
  },
  {
    "port": "0-65535",
    "inboundTag": [],
    "outboundTag": "proxy",
    "domain": [
      "geosite:geolocation-!cn"
    ],
    "enabled": true
  }
]
```

```
#全局规则
[
  {
    "outboundTag": "block",
    "domain": [
      "geosite:category-ads-all"
    ],
    "enabled": true
  },
  {
    "port": "0-65535",
    "inboundTag": [],
    "outboundTag": "proxy",
    "enabled": true
  }
]
```

```
#直连规则
[
  {
    "outboundTag": "block",
    "domain": [
      "geosite:category-ads-all"
    ],
    "enabled": true
  },
  {
    "port": "0-65535",
    "inboundTag": [],
    "outboundTag": "direct",
    "ip": [],
    "domain": [],
    "protocol": [],
    "enabled": true
  }
]
```