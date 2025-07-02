# StarVPN

StarVPN is an easy-to-use self-hosted VPN service, supporting multi-platform and Docker quick deployment, suitable for personal and team secure networking.

## Main Features
- Multi-platform client support
- Simple web management UI
- Account/password login
- One-click Docker deployment
- High performance, secure and stable

## Quick Deployment (Docker Example)
```yaml
version: "3"
services:
  starvpn:
    image: starvpn/starvpn:latest
    container_name: starvpn
    environment:
      - STARS_USER=xxxxx # User username
      - STARS_PASS=xxxxx # User password
    ports:
      - "8080:8080" # Web management port
    volumes:
      - ./starvpn-data:/data
    restart: always
```

## Parameter Description
- **STARS_USER**:  username
- **STARS_PASS**:  password
- **8080**: Web management port
- **/data**: Data persistence directory

## FAQ
- Default username/password is admin/admin. Please change it after first deployment.
- Multi-platform clients supported, see official docs.
- To customize port or directory, edit the compose file accordingly.

## Official Docs & Support
- Website: [https://starvpn.cn/](https://starvpn.cn/)
- Docs: [https://doc.starvpn.cn/#/docker](https://doc.starvpn.cn/#/docker)
- GitHub: [https://github.com/starvpn/starvpn](https://github.com/starvpn/starvpn) 