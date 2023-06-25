```
#代理规则
[
  {
    "id": "5123167661275547155",
    "port": "",
    "outboundTag": "block",
    "domain": [
      "geosite:category-ads-all"
    ],
    "enabled": true
  },
  {
    "id": "5682099627238664576",
    "port": "",
    "outboundTag": "proxy",
    "ip": [],
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
    "id": "5702461616623230001",
    "port": "",
    "outboundTag": "direct",
    "ip": [],
    "domain": [
      "domain:caseu.ml",
      "domain:jutal.com",
      "domain:moyu.im",
      "domain;pjoe.com.cn",
      "geosite:apple",
      "geosite:category-games@cn",
      "geosite:cn",
      "#geosite:microsoft",
      "geosite:private",
      "geosite:win-extra",
      "geosite:win-spy",
      "geosite:win-update"
    ],
    "enabled": true
  },
  {
    "id": "4953195308297413876",
    "port": "",
    "outboundTag": "direct",
    "ip": [
      "geoip:cn",
      "geoip:private"
    ],
    "domain": [],
    "enabled": true
  },
  {
    "id": "4644242632582213581",
    "port": "",
    "outboundTag": "proxy",
    "ip": [],
    "domain": [
      "geosite:geolocation-!cn",
      "geosite:gfw",
      "geosite:tld-!cn"
    ],
    "enabled": true
  },
  {
    "id": "4685181203966893939",
    "port": "",
    "outboundTag": "proxy",
    "ip": [
      "geoip:!cn"
    ],
    "domain": [],
    "enabled": true
  }
]
```

```
#全局规则
[
  {
    "id": "4675159196742169851",
    "port": "",
    "outboundTag": "block",
    "ip": [],
    "domain": [
      "geosite:category-ads-all"
    ],
    "enabled": true
  },
  {
    "id": "5715606251948465282",
    "port": "0-65535",
    "outboundTag": "proxy",
    "ip": [],
    "domain": [],
    "enabled": true
  }
]
```

```
#直连规则
[
  {
    "id": "4671643984874062057",
    "port": "",
    "outboundTag": "block",
    "ip": [],
    "domain": [
      "geosite:category-ads-all"
    ],
    "enabled": true
  },
  {
    "id": "5099340740322730435",
    "port": "0-65535",
    "outboundTag": "direct",
    "ip": [],
    "domain": [],
    "enabled": true
  }
]
```