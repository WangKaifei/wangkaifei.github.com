---
layout: post
title: 本地使用 Docker 部署 Pandora for ChatGPT
---
### 前提
1. 会上网
2. 会用 Docker

### 步骤
1. 登录 https://chat.openai.com
2. 访问 https://chat.openai.com/api/auth/session 获取 accessToken
3. 编写 docker-compose.yaml
	```yaml
	version: '3.5'
	services:
	  pandora-chatgpt:
	    image: "pengzhile/pandora"
	    restart: always
	    container_name: pandora-chatgpt
	    ports:
	    - "8000:8000"
	    environment:
	    - PANDORA_SERVER=0.0.0.0:8000
	    - PANDORA_ACCESS_TOKEN=获取的accessToken
	```
4. 执行 `docker-compose up -d`

操作完毕后，访问 http://127.0.0.1:8000 、http://0.0.0.0:8000 或 http://内网IP:8000 均可访问。