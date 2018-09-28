# v2ray 一键部署 heroku [![Deploy](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy?template=https://github.com/wangyi2005/v2ray-heroku)
V2ray-Core 3.9

1.服务端部署后，应 open app ，显示 Bad Request，表示部署成功。

2.客户端应使用websocket+tls传输协议。Vmess协议的 users id 应当换成自己的UUID，"alterId": 64
# v2ray 部署在 openshift V3
搜索本镜像

环境变量： CONFIG_JSON（配置）

{
  "log": {
    "loglevel": "warning"
  },
  "inbound": {
    "protocol": "vmess",
    "port": 8080,
    "settings": {
      "clients": [
        {
          "id": "fa903dad-5761-4664-aa8b-aea666675de3",
          "alterId": 64
        }
      ]
    },
    "streamSettings": {
      "network": "ws"
    }
  },
  "inboundDetour": [],
  "outbound": {
    "protocol": "freedom",
   "settings": {}
  }
}

用notepad++将上述变量中 \r\n 替换为\\\n，变成一行，导入容器。

客户端： android Actinium、windows v2ray 可用同一个服务端。
