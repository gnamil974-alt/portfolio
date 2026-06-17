# My Portfolio — CLAUDE.md

## 프로젝트 개요
디자이너 겸 퍼블리셔를 위한 개인 포트폴리오 웹사이트

## 기술 스택
- **Framework**: Vue 3 (Composition API, `<script setup>`)
- **Build Tool**: Vite 5 (Node.js v21 호환 버전)
- **Styling**: SCSS (컴포넌트 scoped + 전역 변수)
- **언어**: JavaScript (ES Modules)
- **마크업**: HTML5 시멘틱 마크업
- **브라우저 지원**: Chrome / Firefox / Safari / Edge 최신 2버전

## 디자인 시스템

### 컬러
- `--color-bg`: #fbf4e4 ← 메인 배경색
- `--color-text`: #232323 ← 기본 폰트 컬러
- `--color-accent`: #FF1B00 ← 포인트 컬러

### 타이포그래피
- **Headline**: `Canela Text Trial` (세리프 헤드라인 전용)
- **모든 텍스트**: `Inter` (본문, UI, 레이블 등 나머지 전체)

### 기본 원칙
- 심플하지만 고급스러운 느낌
- `#fbf4e4` 베이지 베이스, `#FF1B00` 포인트
- 충분한 여백 (여백이 고급스러움을 만든다)
- 부드러운 전환 애니메이션 (`--transition: 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94)`)

## 반응형 브레이크포인트 (모바일 퍼스트)

| 구간 | 기준 | 비고 |
|------|------|------|
| Mobile | 375px 기준 | 기본(베이스) 스타일 |
| Tablet | 768px 이상 | `@media (min-width: 768px)` |
| Desktop | 1280px 이상 | `@media (min-width: 1280px)` |

> 모바일 퍼스트 방식 — 모바일 스타일을 기본으로 작성 후 min-width로 확장

## 프로젝트 구조
```
src/
  components/
    layout/
      AppHeader.vue     — 상단 네비게이션 (로고 + 메뉴 + 모바일 풀스크린 메뉴)
      AppFooter.vue     — 하단 푸터
    sections/
      HeroSection.vue      — 첫 화면 인트로
      AboutSection.vue     — 자기소개 + 멤버 그리드
      WorkSection.vue      — 수행이력 (타임라인)
      PortfolioSection.vue — 작업 결과물 (가로 스와이퍼)
      ContactSection.vue   — 연락처 (이메일 + SNS)
  App.vue
  main.js
  style.scss           — 전역 CSS 변수, 리셋, 공통 유틸
```

## 개발 규칙

### 마크업
- HTML5 시멘틱 태그 사용 (`<header>`, `<main>`, `<section>`, `<nav>`, `<footer>` 등)
- 클래스명: **OOCSS 방법론** (구조와 스킨 분리)
- 들여쓰기: **2 spaces** (탭 금지)

### 접근성 (WCAG 2.1 AA 기준)
- 모든 `<img>`에 `alt` 속성 필수
- 모든 `<button>`에 `aria-label` 명시
- 키보드 접근성 보장 (Tab 순서, focus 스타일)
- 충분한 색상 대비 확보

### 스타일
- Composition API (`<script setup>`) 사용
- 컴포넌트별 scoped SCSS
- 전역 CSS 변수·믹스인은 `style.scss`에서만 정의
- 브레이크포인트: 375px / 768px / 1280px (min-width 기준)
- 이미지는 `src/assets/` 하위에 정리
- 더미 데이터는 컴포넌트 내부에 직접 작성

## 실행 방법
```bash
npm run dev     # 개발 서버 (http://localhost:5173)
npm run build   # 프로덕션 빌드
npm run preview # 빌드 결과 미리보기
```

> **참고**: Node.js v21에서는 `npx vite` 또는 `.\node_modules\.bin\vite` 로 직접 실행
> (npm run dev 실행 경로 문제 발생 시)
