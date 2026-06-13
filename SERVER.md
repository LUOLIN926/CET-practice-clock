# 服务器信息

## 连接方式

- 公网 IP：`8.148.198.20`
- 内网 IP：`172.24.154.79`
- SSH 端口：`22`
- 用户名：`root`
- 密码：见 `scripts/.env`（`SERVER_PASS` 字段，已 gitignore）
- 连接命令：`ssh root@8.148.198.20`

## 域名与 SSL

- 域名：`examclock.cn` / `www.examclock.cn`
- SSL 证书：Let's Encrypt（自动续期）
- 证书路径：`/etc/letsencrypt/live/examclock.cn/`
- HTTP 自动 301 跳转至 HTTPS

## Web 部署

- Nginx 配置：`/etc/nginx/nginx.conf`
- Web 根目录：`/usr/share/nginx/html/examclock`
- 监听端口：80（HTTP）/ 443（HTTPS）

## 部署流程

使用 `scripts/deploy.sh` 一键部署，脚本会自动：

1. 打包项目文件（排除 .git、scripts、design.html 等非部署文件）
2. 上传并解压到服务器 Web 根目录
3. 清理旧文件
4. 注入备案信息（ICP）到 HTML 页面 bottom-bar 最下方
5. 重载 Nginx

运行方式：
```bash
source scripts/.env && SERVER_PASS=$SERVER_PASS bash scripts/deploy.sh
```

## 备案信息

服务器部署版本必须包含备案信息（法律要求），GitHub 仓库不包含：

- ICP 备案号：见 `scripts/.env`（`ICP_ICP_NUMBER`）
- 公安备案号：见 `scripts/.env`（`ICP_GA_NUMBER`）
- 公安图标：`assets/images/ga_icon.png`（仅服务器端，已 gitignore）
