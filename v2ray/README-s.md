1. 定域名，比如说：aa.liyu2020.ml, 解析域名

2. 安装git，docker，docker-compose
yum -y install git

git clone https://github.com/hanjun806/v2ray-docker.git

yum install epel-release - y
yum install docker-io - y
systemctl start docker
systemctl enable docker.service

curl -L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

chmod +x /usr/local/bin/docker-compose

ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
3. 修改域名替换

sed -i "s/cc.liyu2020.ml/aa.liyu2020.ml/g" `grep -rl cc.liyu2020.ml`
chmod +x init-letsencrypt.sh
./init-letsencrypt.sh

4. 配置客户端

"inbounds": [
    {
      "port": 30909,
      "listen": "0.0.0.0",
      "protocol": "vmess",
      "settings": {
        "clients": [
          {
            "id": "e62f0d68-baea-411c-9fb6-9ddfe731e11a",
            "level": 1,
            "alterId": 64
          }
        ]
      },
      "streamSettings": {
        "network": "ws",
        "wsSettings": {
          "path": "/v2ray"
        }
      }
    }
  ]