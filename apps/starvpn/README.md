# StarVPN

StarVPN 是一款简单易用的自托管 VPN 服务，支持多平台和 Docker 快速部署，适合个人和团队安全上网。

## 主要功能
- 支持多平台客户端接入
- 简单易用的 Web 管理界面
- 支持账号密码登录
- 支持 Docker 一键部署
- 高性能、安全稳定

## 快速部署（Docker 示例）
```yaml
version: "3"
services:
  starvpn:
    image: starvpn/starvpn:latest
    container_name: starvpn
    environment:
      - STARS_USER=admin # 管理员账号
      - STARS_PASS=admin # 管理员密码
    ports:
      - "8080:8080" # Web 管理端口
    volumes:
      - ./starvpn-data:/data
    restart: always
```

## 参数说明
- **STARS_USER**：Web 管理员账号
- **STARS_PASS**：Web 管理员密码
- **8080**：Web 管理端口
- **/data**：数据持久化目录

## 常见问题 FAQ
- 默认账号密码为 admin/admin，建议首次部署后及时修改。
- 支持多平台客户端，详见官方文档。
- 如需自定义端口或目录，请修改 compose 文件对应参数。

## 官方文档与支持
- 官网：[https://starvpn.cn/](https://starvpn.cn/)
- 文档：[https://doc.starvpn.cn/#/docker](https://doc.starvpn.cn/#/docker)
- GitHub：[https://github.com/starvpn/starvpn](https://github.com/starvpn/starvpn) 