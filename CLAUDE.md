# My Portfolio — CLAUDE.md

## 프로젝트 개요
디자이너 겸 퍼블리셔를 위한 개인 포트폴리오 웹사이트

## 기술 스택
- **Framework**: Vue 3 (Composition API, `<script setup>`)
- **Build Tool**: Vite 5 (Node.js v21 호환 버전 — v8은 Node 20.19+/22.12+ 필요)
- **Styling**: CSS (컴포넌트 scoped + 전역 변수)
- **언어**: JavaScript (ES Modules)

## 디자인 시스템

### 컬러
- `--color-white`: #FFFFFF
- `--color-off-white`: #F7F7F5
- `--color-black`: #0A0A0A
- `--color-dark`: #1A1A1A
- `--color-gray`: #6B6B6B
- `--color-gray-light`: #E5E5E3
- `--color-green`: #2A7A4F  ← 포인트 컬러
- `--color-green-light`: #3D9965
- `--color-green-muted`: #EAF3EE

### 타이포그래피
- **제목**: `Playfair Display` (고급스러운 세리프체)
- **본문**: `Inter` (깔끔한 산세리프체)
- **영문 강조**: `Cormorant Garamond`

### 기본 원칙
- 심플하지만 고급스러운 느낌
- 화이트/블랙 베이스, 그린 포인트
- 충분한 여백 (여백이 고급스러움을 만든다)
- 부드러운 전환 애니메이션 (`--transition: 0.4s cubic-bezier(...)`)

## 반응형 브레이크포인트

| 구간 | 기준 | 주요 변화 |
|------|------|-----------|
| Desktop | > 1024px | 기본 레이아웃 |
| Tablet | ≤ 1024px | gap·padding 축소 |
| Mobile | ≤ 768px | 단일 컬럼, 햄버거 메뉴 |
| Small | ≤ 480px | 폰트·패딩 추가 축소 |

### 반응형 주요 동작
- **AppHeader**: 768px 이하에서 nav 숨김 → 햄버거 메뉴(슬라이드인) 표시
- **AppHeader 색상**: Hero 위(미스크롤) = 흰 텍스트(`.on-dark`), 스크롤 후 = 검정 텍스트 + 흰 배경
- **HeroSection**: `100svh` 사용(모바일 safe area), 스크롤 힌트 768px 이하 숨김
- **AboutSection**: 768px에서 2열 → 1열, 480px에서 스킬 2열
- **WorkSection**: 768px에서 날짜 열 숨김 → 카드 내부(`.card-period-mobile`)에 표시
- **PortfolioSection**: 768px에서 헤더 세로 배치, 모바일 오버레이 항상 표시, 480px에서 1열
- **ContactSection**: 768px에서 2열 → 1열, `email-address` clamp로 유동 크기

## 프로젝트 구조
```
src/
  components/
    layout/
      AppHeader.vue     — 상단 네비게이션 (로고 + 메뉴 + 모바일 풀스크린 메뉴)
      AppFooter.vue     — 하단 푸터
    sections/
      HeroSection.vue   — 첫 화면 인트로 (풀스크린 다크)
      AboutSection.vue  — 자기소개 + 스킬
      WorkSection.vue   — 수행이력 (타임라인)
      PortfolioSection.vue — 작업 결과물 (필터 + 그리드 갤러리)
      ContactSection.vue   — 연락처 (이메일 + SNS)
  App.vue
  main.js
  style.css            — 전역 CSS 변수, 리셋, 공통 유틸(.container, .section, .section-label, .section-title)
```

## 섹션 구성
1. **Hero** — 풀스크린 다크 인트로, 이름 + 직함 + 슬로건 + CTA
2. **About** — 자기소개 텍스트 + 프로필 사진 자리 + 스킬 3열
3. **Work** — 수행이력 타임라인 (회사/역할/설명/태그)
4. **Portfolio** — 카테고리 필터 + 비대칭 그리드 갤러리 (hover 오버레이)
5. **Contact** — 이메일 블록 + SNS 링크 (다크 배경)

## 개발 규칙
- Composition API (`<script setup>`) 사용
- 컴포넌트별 scoped CSS
- 전역 CSS 변수는 `style.css`에서만 정의
- 브레이크포인트는 1024px / 768px / 480px 3단계로 통일
- 이미지는 `src/assets/` 하위 폴더에 정리
- 더미 데이터는 컴포넌트 내부에 직접 작성 (추후 별도 data 파일로 분리 가능)

## 실행 방법
```bash
npm run dev     # 개발 서버 (http://localhost:5173)
npm run build   # 프로덕션 빌드
npm run preview # 빌드 결과 미리보기
```

> **참고**: Node.js v21에서는 `npx vite` 또는 `.\node_modules\.bin\vite` 로 직접 실행
> (npm run dev 실행 경로 문제 발생 시)
