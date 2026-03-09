# Content Guide

## 문서 작성 위치

모든 문서는 `content/docs/` 안에 `.mdx` 파일로 작성.

## MDX 파일 구조

```mdx
---
title: 페이지 제목
description: 페이지 설명 (SEO, 검색에 사용)
---

# 본문 시작

마크다운 + JSX 컴포넌트 사용 가능
```

## 사이드바 관리 (meta.json)

각 폴더에 `meta.json`을 만들어 메뉴 순서와 그룹을 정의:

```json
{
  "title": "섹션 제목",
  "description": "섹션 설명",
  "pages": [
    "index",
    "quickstart",
    "---Getting Started---",
    "essentials",
    "features"
  ]
}
```

- 파일명(확장자 제외)으로 참조
- `"---제목---"` 형식으로 구분선/그룹 헤더 추가 가능
- 폴더명으로 하위 섹션 참조

## 새 문서 추가 순서

1. `content/docs/` 적절한 위치에 `.mdx` 파일 생성
2. 해당 폴더의 `meta.json`에 파일명 추가
3. dev 서버에서 확인 (`npm run dev`)

## 새 섹션(폴더) 추가

1. `content/docs/` 아래 새 폴더 생성
2. 폴더 안에 `meta.json` 작성 (title, pages)
3. 상위 폴더의 `meta.json`에 폴더명 추가

## 지원하는 MDX 기능

- **코드 블록**: 신택스 하이라이팅 (Shiki), 코드 탭
- **수학**: KaTeX (`$수식$`, `$$블록수식$$`)
- **다이어그램**: Mermaid (```mermaid 코드블록)
- **TypeScript**: Twoslash 타입 표시
- **Steps**: 단계별 가이드 (`<Steps>` 컴포넌트)
- **Callout**: 정보/경고 박스
- **GFM**: 테이블, 체크리스트 등
