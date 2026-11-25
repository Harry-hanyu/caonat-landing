# CAONAT Landing — progress

## Status（2026-11-25）
- **Live**: https://www.caonat.vip （香港 ECS nginx + Let’s Encrypt）
- **官网 ECS**：`i-j6c9ad3tdqv8nwe7wltl` / `47.238.76.36` / 区域 `cn-hongkong` / webroot `/var/www/caonat`
- **采集 ECS（杭州）**：`i-bp1fh39fq2qo2le4n1e5` / `118.178.99.35` — 也有旧 `/var/www/caonat` 副本，**DNS 不指向它**
- **TikTok Ads 回调**：
  - `/oauth/tiktok/callback/` 已上线
  - 根路径 `/?auth_code=…` 会自动 `location.replace` 到回调页（与应用后台 redirect=`https://www.caonat.vip/` 一致）
- **本机**：`/Users/golong/Projects/caonat-landing`
- **凭据**：`~/.cursor/local/hanlu-tiktok-ads.env`

## 验证
```bash
curl -sk https://www.caonat.vip/oauth/tiktok/callback/ | head
curl -sk 'https://www.caonat.vip/?auth_code=TEST&state=x' | rg location.replace
```

## 下一步
1. 浏览器打开广告主授权 URL（env 里 `TIKTOK_ADS_ADVERTISER_AUTH_URL`）完成授权
2. 回调页复制 auth_code → `python3 ~/Projects/hanlu-odps-sync/scripts/tiktok_ads_exchange_token.py --auth-code '…'`
3. （可选）门户邮箱验证码通过后，把后台 redirect 改成专用 callback 路径
