# 도메인 & 접근 제어 - 완료

## 결과

- **도메인**: `https://gemgem-docs.tinysolver.me`
- **DNS**: Terraform CNAME → `cname.vercel-dns.com` (Cloudflare 프록시 활성화)
- **SSL**: Cloudflare Edge SSL
- **접근 제어**: Cloudflare Access — `@gemgem.me` 이메일만 허용 (OTP 인증)
- **Vercel**: `gemgem-beginner-get-started` 프로젝트에 연결됨

## 구조

```
tinysolver.me (Cloudflare)
├── *.tinysolver.me              → Cloudflare Tunnel (와일드카드)
├── gemgem.tinysolver.me         → Tunnel → Coolify 대시보드
└── gemgem-docs.tinysolver.me    → Cloudflare Access → Vercel (이 사이트)
```

## IaC

- Terraform: `gemgem-devops/terraform/main.tf`
  - `cloudflare_dns_record.gemgem_docs` — DNS CNAME
  - `cloudflare_zero_trust_access_application.gemgem_docs` — 접근 제어
- 상세 문서: [gemgem-devops/docs/external-domains.md](https://github.com/candy-gemgem/gemgem-devops/blob/main/docs/external-domains.md)

## TODO

- [ ] Cloudflare Access 로그인 방식 정리 (현재 Google + OTP 기본 제공 → IdP 제한 or 커스터마이징)
  - Terraform: `allowed_idps`, `auto_redirect_to_identity` 등 설정
