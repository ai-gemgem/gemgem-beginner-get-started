# Deployment

## Vercel 배포

### 수동 배포
```bash
vercel --prod
```

### 자동 배포
GitHub repo 연결 시 `main` 브랜치 push → 자동 배포

## 환경변수

| 변수 | 위치 | 용도 |
|------|------|------|
| `ANTHROPIC_API_KEY` | Vercel 환경변수 (production) | AI 챗봇 |
| `NEXT_PUBLIC_BASE_URL` | Vercel 환경변수 (production) | 사이트 기본 URL |

### 로컬 개발
`.env.local` 파일에 설정:
```
ANTHROPIC_API_KEY="sk-ant-xxx"
NEXT_PUBLIC_BASE_URL="http://localhost:3000"
```

## Vercel 프로젝트 정보

- **Team**: gemgem-candykims-projects
- **Project**: gemgem-beginner-get-started
- **URL**: https://gemgem-beginner-get-started.vercel.app
- **Dashboard**: https://vercel.com/gemgem-candykims-projects/gemgem-beginner-get-started

## 빌드 명령어

```bash
npm run dev        # 로컬 개발 서버
npm run build      # 프로덕션 빌드 (pre-build 스크립트 포함)
npm run start      # 빌드된 앱 실행
```

## GitHub 저장소

- **Org**: ai-gemgem
- **Repo**: https://github.com/ai-gemgem/gemgem-beginner-get-started
