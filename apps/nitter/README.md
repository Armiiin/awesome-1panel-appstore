# Nitter 介绍

## 产品介绍

Nitter 是一款免费开源、注重隐私的 Twitter/X 替代前端。它不依赖 JavaScript、无广告、无追踪、无付费墙，无需登录即可浏览推文、时间线和搜索内容，适合自建部署后匿名使用 Twitter/X。

本应用同时内置 Redis 服务用于缓存，安装后开箱即用，无需在 1Panel 中单独安装 Redis。

## 主要功能

- **隐私友好**：无需登录、无追踪、无广告、无 JavaScript
- **简洁快速**：页面轻量，浏览推文和媒体更省流量
- **RSS 支持**：内置 RSS 订阅，可订阅用户、列表和搜索关键词
- **多主题**：支持多套界面主题，可自定义替换链接与偏好设置
- **内置 Redis 缓存**：提升访问性能，减少对 Twitter/X 的重复请求
- **多架构支持**：镜像同时支持 amd64 与 arm64

## 使用说明

1. 安装后访问 `http://服务器IP:端口`。
2. 主要配置均保存在 `nitter.conf` 文件中，位于应用安装目录的 `data/` 文件夹下：
   - 修改 `[Server]` 中的 `hostname` 为你的域名或 IP，用于生成正确链接。
   - 修改 `[Config]` 中的 `hmacKey` 为随机值（可用 `openssl rand -hex 32` 生成），用于签名媒体链接。
   - 如需 HTTPS 访问，建议通过反向代理（如 1Panel 网站）配置，并将 `https` 保持为 `false`。
3. 修改配置后需重启应用生效。
4. Redis 数据保存在 `data/redis` 目录下，缓存可安全清理，不影响使用。

## 注意事项

- `nitter.conf` 必须存在，请勿删除或改名为目录。
- 若需使用 Cookie 会话（可选），可在 `data/` 下放置 `sessions.jsonl` 并参考官方文档挂载到容器内。

## 相关链接

- [Nitter 官方仓库](https://github.com/zedeus/nitter)
- [Nitter 官方文档](https://github.com/zedeus/nitter/blob/master/README.md)
