# Architecture

## 렌더링 흐름

```
content/docs/*.mdx → source.config.ts (MDX 파싱) → src/app/docs/[[...slug]]/page.tsx (렌더링)
```

## 디렉토리 상세

### content/docs/ (콘텐츠 원본)

```
content/docs/
├── meta.json                    ← 최상위 사이드바: ["(index)", "api-reference", "changelog"]
├── (index)/                     ← 메인 문서 섹션
│   ├── meta.json                ← 섹션 내 메뉴 순서 & 그룹 정의
│   ├── index.mdx                ← /docs 소개 페이지
│   ├── quickstart.mdx           ← /docs/quickstart
│   ├── essentials/              ← 하위 섹션
│   ├── features/
│   └── guides/
├── api-reference/               ← OpenAPI 기반 자동생성 문서
│   ├── openapi.yml              ← OpenAPI 스펙 원본
│   └── (generated)/             ← 빌드 시 자동생성 (직접 수정 X)
└── changelog/
```

### src/app/ (Next.js 앱 라우터)

```
src/app/
├── (home)/page.tsx              ← 랜딩 페이지 (/)
├── docs/
│   ├── layout.tsx               ← 문서 레이아웃 (사이드바 + AI 챗봇 탑재)
│   └── [[...slug]]/page.tsx     ← MDX → HTML 렌더링 동적 라우트
├── api/
│   ├── chat/route.ts            ← AI 챗봇 API (POST /api/chat)
│   ├── search/route.ts          ← 문서 검색 API (GET /api/search)
│   └── proxy/route.ts           ← 프록시 API
├── og/[...slug]/                ← OpenGraph 이미지 자동생성
├── llms.txt/                    ← LLM용 문서 텍스트 제공
├── rss.xml/                     ← RSS 피드
└── sitemap.ts                   ← 사이트맵
```

### src/lib/ (유틸리티)

- `source.tsx` - fumadocs 소스 로더 (content/docs → 페이지 데이터)
- `layout.shared.tsx` - 네비게이션 링크, 사이트 이름 설정
- `metadata.ts` - SEO 메타데이터 생성
- `shiki.ts` - 코드 신택스 하이라이팅 설정
- `constants/` - 카테고리, 태그 상수

## 설정 파일

| 파일 | 역할 |
|------|------|
| `source.config.ts` | fumadocs MDX 파싱 (플러그인, frontmatter 스키마) |
| `next.config.ts` | Next.js 설정 (MDX 지원, 이미지 패턴, 리라이트) |
| `tsconfig.json` | TypeScript (경로 별칭: `@/*` → `./src/*`) |
| `components.json` | shadcn/ui 설정 |
| `postcss.config.js` | PostCSS + Tailwind |
