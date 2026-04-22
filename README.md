支持 文生图、图生图编辑、多图合成，模型包括非常强大的 gpt-image-2 ，并且还没有某包那样的水印

![b4d7752629dac4e31eb7a09761905f69.png](../_resources/b4d7752629dac4e31eb7a09761905f69.png)

提供账号池管理，Docker 一键部署

![171fce8cff8b899985c4fd77a940b3fe.png](../_resources/171fce8cff8b899985c4fd77a940b3fe.png)

项目地址：https://github.com/basketikun/chatgpt2api

推荐服务器部署，不要选择国内地区，选择Linux版本Docker上手快

腾讯云新加坡，硅谷，东京地区价格是199元一年，2核4G30M带宽，60GBSSD盘 1.5T月流量，推荐硅谷地区CN2线路↓↓↓，系统选Ubuntu24

购买地址：https://curl.qcloud.com/oyWDLkRJ

![72d493eab65af6588b3ed9cb7585b177.png](../_resources/72d493eab65af6588b3ed9cb7585b177.png)

**教程**

1.安装Docker

```
sudo apt update
sudo apt install -y ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo docker run hello-world
```

![1b55ecb41568de331b7837106a34f478.png](../_resources/1b55ecb41568de331b7837106a34f478.png)

2.下载项目

```
git clone https://github.com/basketikun/chatgpt2api.git
```

![6c30c3ba3b8489f503b9fd6ecc8a55ee.png](../_resources/6c30c3ba3b8489f503b9fd6ecc8a55ee.png)

3.打开项目

```
 cd chatgpt2api
```

![2a931cd1cbb42d623e73c8d6591ea95c.png](../_resources/2a931cd1cbb42d623e73c8d6591ea95c.png)

4.运行

```
docker compose up -d
```

![be9bb8cbf61b90a40033e0833d94c500.png](../_resources/be9bb8cbf61b90a40033e0833d94c500.png)

5.打开浏览器输入

http://你的服务器公网IP:3000 

记得防火墙放通3000端口

密钥是：chatgpt2api

![77ebddebd919b8c4827d1ef153911885.png](../_resources/77ebddebd919b8c4827d1ef153911885.png)

6.导入账号选择：**导入Session JSON**

![bbf7e2ed2e956358bc8cdf46cebd624e.png](../_resources/bbf7e2ed2e956358bc8cdf46cebd624e.png)

7.打开以下地址，复制页面返回的完整 JSON，系统会自动提取其中的 `accessToken` 导

https://chatgpt.com/api/auth/session

![60402961b5c49b5dfa11d63c05663efe.png](../_resources/60402961b5c49b5dfa11d63c05663efe.png)

8.导入成功

![379270ac146b2a9e040291a88ff65821.png](../_resources/379270ac146b2a9e040291a88ff65821.png)

9.点击顶部的画图

![be37cf15f64404da2e63d8d8a94a6f2d.png](../_resources/be37cf15f64404da2e63d8d8a94a6f2d.png)

10.模型可以切换为gpt-image-2 ，额度剩余7

![0e5ef3be8bba1adc9911ee10b7c06ffc.png](../_resources/0e5ef3be8bba1adc9911ee10b7c06ffc.png)

11.提示词：生成一个女生在抖音直播

效果非常强大

![7b57d7ec22aa431bc1d199c629afd23f.png](../_resources/7b57d7ec22aa431bc1d199c629afd23f.png)

![461a5b44163a0b064e94150e696fee5b.png](../_resources/461a5b44163a0b064e94150e696fee5b.png)

OpenAI 兼容图片生成接口，用于文生图

```
curl http://localhost:8000/v1/images/generations \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <auth-key>" \
  -d '{
    "model": "gpt-image-2",
    "prompt": "一只漂浮在太空里的猫",
    "n": 1,
    "response_format": "b64_json"
  }'
```

  模型：gpt-image-2

  密钥：chatgpt2api

  按需编辑 config.json 的密钥，编辑后需要重启Docker