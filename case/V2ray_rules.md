```
#代理规则
[
  {
    "inboundTag": [],
    "outboundTag": "proxy",
    "domain": [
      "domain:openai.com",
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
      "domain:jutal.com",
      "domain:moyu.im",
      "domain:caseu.ml",
      "domain;pjoe.com.cn",
      "geosite:apple",
      "geosite:category-games@cn",
      "geosite:cn",
      "geosite:microsoft",
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
      "geoip:private",
      "168.138.33.156"
    ],
    "enabled": true
  },
  {
    "port": "0-65535",
    "inboundTag": [],
    "outboundTag": "proxy",
    "ip": [
      "geoip:!cn"
    ],
    "domain": [
      "geosite:geolocation-!cn"
    ],
    "enabled": true
  },
  {
    "inboundTag": [],
    "outboundTag": "block",
    "domain": [
      "geosite:category-ads-all"
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