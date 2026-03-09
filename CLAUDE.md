# GemGem Beginner Get Started

AI 입문자를 위한 가이드 문서 사이트. fumadocs + Next.js 기반, Vercel 배포.

## Tech Stack

- **Framework**: Next.js 16 + fumadocs (MDX 문서 프레임워크)
- **AI Chatbot**: Anthropic Claude Sonnet via Vercel AI SDK
- **Styling**: Tailwind CSS 4
- **Deploy**: Vercel

## Project Structure

```
content/docs/          ← 문서 콘텐츠 원본 (MDX). 여기만 편집하면 사이트에 반영됨
src/app/               ← Next.js 앱 라우터 (레이아웃, API, 페이지 렌더링)
src/components/        ← UI 컴포넌트
src/lib/               ← 유틸리티, 설정
source.config.ts       ← fumadocs MDX 파싱 설정
```

## Key Rules

- 문서 콘텐츠는 `content/docs/` 안에서만 작성 (.mdx)
- 사이드바 구조는 각 폴더의 `meta.json`으로 관리
- 환경변수: `ANTHROPIC_API_KEY` (AI 챗봇), `NEXT_PUBLIC_BASE_URL` (사이트 URL)
- 배포: `vercel --prod` 또는 git push → Vercel 자동 배포

## Detailed Docs

- [Architecture](.claude/docs/architecture.md) - 프로젝트 구조 & 렌더링 흐름
- [Content Guide](.claude/docs/content-guide.md) - MDX 콘텐츠 작성 규칙
- [Deployment](.claude/docs/deployment.md) - 배포 & 환경변수 설정
- [AI Chatbot](.claude/docs/ai-chatbot.md) - AI 챗봇 설정 & 커스터마이징
