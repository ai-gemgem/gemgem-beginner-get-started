# AI Chatbot

## 개요

사이트 내장 AI 챗봇. 문서 내용을 검색/조회해서 사용자 질문에 답변.

## 기술 스택

- **SDK**: Vercel AI SDK (`ai`, `@ai-sdk/anthropic`, `@ai-sdk/react`)
- **Model**: `claude-sonnet-4-6` (Anthropic)
- **UI**: `src/components/fumadocs/ai/` 컴포넌트

## 주요 파일

```
src/app/api/chat/
├── route.ts                         ← 메인 엔드포인트 (POST /api/chat)
├── types.ts                         ← 메시지 타입 정의
└── utils/
    ├── llms.ts                      ← LLM 텍스트 생성
    ├── prompts/                     ← 시스템 프롬프트 구성
    │   ├── index.ts                 ← 프롬프트 조합
    │   ├── core.ts                  ← 핵심 지시사항
    │   ├── directives.ts            ← 추가 디렉티브
    │   ├── examples.ts              ← 예시
    │   ├── llms.ts                  ← 문서 컨텍스트
    │   └── tools.ts                 ← 도구 설명
    └── tools/
        ├── search-docs.ts           ← 문서 검색 도구
        └── get-page-content.ts      ← 페이지 내용 조회 도구
```

## AI 도구 (Tools)

1. **searchDocs** - 문서 전문 검색 (쿼리, 태그 필터, 최대 50개 결과)
2. **getPageContent** - 특정 페이지 전체 내용 조회 (경로 기반)

## 모델 변경

`src/app/api/chat/route.ts:52`:
```ts
model: anthropic('claude-sonnet-4-6'),  // 여기서 모델 변경
```

## 시스템 프롬프트 커스터마이징

`src/app/api/chat/utils/prompts/` 안의 파일들을 수정:
- `core.ts` - 챗봇의 기본 성격/역할
- `directives.ts` - 특수 지시사항
- `examples.ts` - 응답 예시

## UI 접근 방법

- 문서 페이지에서 검색 아이콘 클릭
- 키보드 단축키: `Cmd+/` 또는 `/`
- 사이드 패널로 슬라이드인
