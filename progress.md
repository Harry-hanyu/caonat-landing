# CAONAT Landing — progress

## Status
- **Live**: https://caonat.vip （ECS nginx + Let’s Encrypt，非 GitHub Pages）
- **内容**：品牌站（Products / Collections / About / Shop）+ AI 产品图已上线
- **部署**：2026-11-19 从 GitHub `main@fe7492a` zip 拉取到 `/var/www/caonat`
- **本机**：`/Users/golong/Projects/caonat-landing`

## 验证
```bash
curl -sk https://caonat.vip/ | head
curl -sk -o /dev/null -w "%{http_code}\n" https://caonat.vip/images/hero-lifestyle.jpg
```

## 下一步（TikTok 审核）
1. 在 TikTok For Business Developers 用 **https://caonat.vip** 重新提交网站审核
2. 可选：办 ICP / Cloudflare，让 HTTP:80 也不被 Beaver 拦（目前 HTTPS 正常）
3. 勿再依赖 github.io / 第三方托管指纹

## 注意
- ECS `i-bp1fh39fq2qo2le4n1e5` 与 hanlu-odps-sync 共用，部署只动 `/var/www/caonat`，勿动 `/opt/hanlu-odps-sync`
