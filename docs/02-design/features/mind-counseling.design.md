# 심리상담 웹서비스 (Mind Counseling) Design Document

> **Summary**: AI 기반 한국형 온라인 심리상담 플랫폼 — 정적 웹사이트 MVP 설계
>
> **Project**: mind-counseling
> **Version**: 1.0.0
> **Author**: kimminjae413
> **Date**: 2026-04-02
> **Status**: Draft
> **Planning Doc**: [mind-counseling.plan.md](../01-plan/features/mind-counseling.plan.md)

---

## 1. Overview

### 1.1 Design Goals

- **프리미엄 UX**: 따뜻하고 안전한 느낌의 고급 랜딩 페이지
- **단일 페이지 아키텍처**: index.html 하나에 모든 섹션을 담되, 각 기능은 모달/탭으로 분리
- **성능 최적화**: Lighthouse 90+ (Performance, Accessibility, SEO)
- **모바일 퍼스트**: 375px 기준 설계 → 데스크톱 확장

### 1.2 Design Principles

- **Safe Space Design**: 부드러운 모서리, 넉넉한 여백, 판단하지 않는 카피
- **Progressive Disclosure**: 단계별 정보 공개, 부담 최소화
- **Value Before Signup**: 가입 전에 가치를 먼저 경험
- **Accessibility First**: 색상 대비 4.5:1 이상, 키보드 네비게이션

---

## 2. Architecture

### 2.1 Component Diagram

```
┌──────────────────────────────────────────────────────┐
│                    index.html (SPA)                   │
├──────────────────────────────────────────────────────┤
│  [Navigation]                                        │
│  ┌────────────────────────────────────────────────┐  │
│  │ Sections (scroll-based)                        │  │
│  │ ┌──────────┐ ┌──────────┐ ┌──────────────┐   │  │
│  │ │  Hero    │ │ Features │ │ How It Works │   │  │
│  │ └──────────┘ └──────────┘ └──────────────┘   │  │
│  │ ┌──────────┐ ┌──────────┐ ┌──────────────┐   │  │
│  │ │Testimony │ │ Pricing  │ │  Final CTA   │   │  │
│  │ └──────────┘ └──────────┘ └──────────────┘   │  │
│  └────────────────────────────────────────────────┘  │
│  [Footer]                                            │
├──────────────────────────────────────────────────────┤
│  Modals / Overlays                                   │
│  ┌──────────┐ ┌──────────┐ ┌──────────────────┐    │
│  │ AI Chat  │ │Assessment│ │ Mood Check-in   │    │
│  │  Modal   │ │  Modal   │ │    Modal        │    │
│  └──────────┘ └──────────┘ └──────────────────┘    │
│  ┌──────────┐ ┌──────────┐                          │
│  │Counselor │ │Community │                          │
│  │  Modal   │ │  Modal   │                          │
│  └──────────┘ └──────────┘                          │
└──────────────────────────────────────────────────────┘
```

### 2.2 Data Flow

```
User Interaction → JS Event Handler → LocalStorage (persist)
                                    → DOM Update (render)
                                    → Animation (feedback)
```

### 2.3 Dependencies (CDN)

| Library | Version | Purpose |
|---------|---------|---------|
| Tailwind CSS | 3.x (CDN) | 유틸리티 기반 스타일링 |
| AOS.js | 2.3.4 | 스크롤 애니메이션 |
| Lucide Icons | latest | 아이콘 시스템 |
| Pretendard | latest | 한글 웹폰트 |
| Chart.js | 4.x | 감정 히스토리 차트 |

---

## 3. Existing Code Impact Analysis

### 3.1 수정 대상 파일 상세 분석

| 파일 | 현재 역할 | 수정 내용 | 영향 범위 |
|------|----------|----------|----------|
| index.html | 기존 블로그 자동화 페이지 | **전체 교체** → 심리상담 랜딩 | 전체 |
| css/ | 기존 블로그 CSS | **전체 교체** → 새 디자인 시스템 | 전체 |
| js/ | 기존 블로그 JS | **전체 교체** → 새 기능 로직 | 전체 |
| README.md | 기존 블로그 설명 | **전체 교체** → 프로젝트 소개 | 없음 |

### 3.2 의존성 역추적

> 기존 코드를 전체 교체하므로 역추적 불필요. 새로 시작하는 프로젝트.

### 3.3 사이드이펙트 위험 분석

> 기존 코드 전체 교체 — 사이드이펙트 없음

### 3.4 변경 불가 항목 (보호 대상)

| 보호 대상 | 이유 | 파일 위치 | 출처 |
|----------|------|----------|------|
| **해당 없음** | 기존 코드 전체 교체 승인됨 (사용자 확인) | - | 사용자 지시 |
| .git/ | Git 히스토리 보존 | .git/ | 시스템 |
| docs/ | PDCA 문서 보존 | docs/ | PDCA 프로세스 |

---

## 4. UI/UX Design

### 4.1 Color System

```css
:root {
  /* Primary - Sage Green */
  --primary-50:  #f0f7f2;
  --primary-100: #d4eadb;
  --primary-200: #a8d5b6;
  --primary-300: #7dbe92;
  --primary-400: #5fa873;
  --primary-500: #4a9060;  /* Main */
  --primary-600: #3a7a4e;
  --primary-700: #2d5f3d;
  
  /* Secondary - Lavender */
  --secondary-50:  #f5f0fa;
  --secondary-100: #e6d9f2;
  --secondary-200: #cdb3e5;
  --secondary-300: #b48cd8;
  --secondary-400: #9b66cb;
  --secondary-500: #8250b8;  /* Main */
  
  /* Warm - Soft Peach */
  --warm-50:  #fdf6f3;
  --warm-100: #fae8e0;
  --warm-200: #f5d5c8;
  --warm-300: #f0c2b0;
  
  /* Neutral */
  --bg-primary:   #FAF9F6;  /* Off White */
  --bg-secondary: #F5F3EF;
  --text-primary: #2D2D2D;  /* Charcoal */
  --text-secondary: #6B6B6B;
  --text-muted:   #9E9E9E;
  --border:       #E8E5E0;
}
```

### 4.2 Typography

| Element | Font | Size (Mobile) | Size (Desktop) | Weight |
|---------|------|:------------:|:--------------:|:------:|
| H1 (Hero) | Pretendard | 32px | 56px | 700 |
| H2 (Section) | Pretendard | 24px | 40px | 700 |
| H3 (Card) | Pretendard | 18px | 24px | 600 |
| Body | Pretendard | 15px | 16px | 400 |
| Caption | Pretendard | 13px | 14px | 400 |
| Button | Pretendard | 15px | 16px | 600 |

### 4.3 Section Design Specs

#### Section 1: Hero

```
┌──────────────────────────────────────────────────┐
│ [Nav: Logo  Features  상담  검사  커뮤니티  시작] │
├──────────────────────────────────────────────────┤
│                                                  │
│     "마음도 관리가 필요하니까"          [일러스트] │
│                                                  │
│     AI와 전문 상담사가 함께하는                   │
│     당신만의 마음 관리 플랫폼                     │
│                                                  │
│     [무료로 시작하기]  [서비스 알아보기]           │
│                                                  │
│     ✓ 3만+ 사용자  ✓ 전문 상담사 200+            │
│     ✓ 평균 만족도 4.8                            │
│                                                  │
└──────────────────────────────────────────────────┘
```

#### Section 2: Features (4 Cards)

```
┌────────────┐ ┌────────────┐ ┌────────────┐ ┌────────────┐
│ 🤖         │ │ 📋         │ │ 😊         │ │ 👤         │
│ AI 상담    │ │ 심리검사   │ │ 감정체크인  │ │ 전문상담   │
│            │ │            │ │            │ │            │
│ 24시간     │ │ PHQ-9      │ │ 매일의     │ │ 검증된     │
│ AI 대화   │ │ GAD-7      │ │ 감정 기록  │ │ 전문상담사 │
│ 상담      │ │ 자가진단   │ │ & 분석     │ │ 매칭      │
│            │ │            │ │            │ │            │
│ [체험하기] │ │ [검사하기] │ │ [기록하기] │ │ [상담사↗] │
└────────────┘ └────────────┘ └────────────┘ └────────────┘
```

#### Section 3: How It Works (3 Steps)

```
  ① 감정 체크인          ② AI 상담           ③ 전문 연결
  ┌──────────┐          ┌──────────┐         ┌──────────┐
  │ 오늘의   │ ──────▶ │ AI와     │ ──────▶ │ 필요 시  │
  │ 기분을   │          │ 대화로   │         │ 전문     │
  │ 기록     │          │ 마음     │         │ 상담사   │
  │          │          │ 돌봄     │         │ 연결     │
  └──────────┘          └──────────┘         └──────────┘
```

#### Section 4: Testimonials (Carousel)

```
┌──────────────────────────────────────────────────┐
│  "처음엔 AI 상담이 도움이 될까 했는데,           │
│   매일 감정을 기록하면서 제 마음의 패턴을         │
│   이해하게 되었어요."                             │
│                                                  │
│   — 김○○, 29세, 마케터                           │
│                                                  │
│   ○ ● ○                                          │
└──────────────────────────────────────────────────┘
```

#### Section 5: Pricing (3 Tiers)

```
┌────────────┐  ┌─────────────────┐  ┌────────────┐
│ Free       │  │ 🌟 베이직       │  │ 프로       │
│            │  │    POPULAR      │  │            │
│ ₩0        │  │ ₩9,900/월      │  │ ₩49,900/월 │
│            │  │                 │  │            │
│ · AI 3회  │  │ · AI 무제한    │  │ · 베이직+  │
│ · 체크인  │  │ · 프리미엄     │  │ · 1:1 상담 │
│ · 검사1회 │  │ · 분석 리포트  │  │ · 화상/음성│
│            │  │ · 할인 쿠폰   │  │ · 상담리포트│
│ [시작하기] │  │ [시작하기]     │  │ [시작하기]  │
└────────────┘  └─────────────────┘  └────────────┘
```

#### Section 6: Final CTA

```
┌──────────────────────────────────────────────────┐
│  (gradient background)                           │
│                                                  │
│     오늘, 당신의 마음에                          │
│     첫 번째 안부를 물어보세요                     │
│                                                  │
│     [지금 무료로 시작하기]                        │
│                                                  │
└──────────────────────────────────────────────────┘
```

### 4.4 Modal Design Specs

#### AI Chat Modal

```
┌──────────────────────────────────┐
│ 🤖 AI 마음 상담           [✕]  │
├──────────────────────────────────┤
│                                  │
│  ┌──────────────────────┐       │
│  │ 안녕하세요! 오늘     │       │
│  │ 기분이 어떠세요?     │       │
│  └──────────────────────┘       │
│                                  │
│         ┌──────────────────────┐ │
│         │ 요즘 스트레스를     │ │
│         │ 많이 받고 있어요    │ │
│         └──────────────────────┘ │
│                                  │
│  ┌──────────────────────┐       │
│  │ 스트레스를 받고       │       │
│  │ 계시는군요. 어떤      │       │
│  │ 상황인지 더 이야기    │       │
│  │ 해주실 수 있나요?    │       │
│  └──────────────────────┘       │
│                                  │
├──────────────────────────────────┤
│ [메시지를 입력하세요...]  [전송] │
└──────────────────────────────────┘
```

#### Assessment Modal (PHQ-9)

```
┌──────────────────────────────────┐
│ 📋 우울 자가진단 (PHQ-9)  [✕]  │
├──────────────────────────────────┤
│  질문 3/9          ████░░░░ 33% │
│                                  │
│  지난 2주 동안, 잠들기 어렵거나  │
│  너무 많이 자는 문제로           │
│  얼마나 자주 시달렸나요?        │
│                                  │
│  ○ 전혀 없음                    │
│  ● 며칠 동안                    │
│  ○ 1주일 이상                   │
│  ○ 거의 매일                    │
│                                  │
│  [이전]              [다음 →]   │
└──────────────────────────────────┘
```

#### Mood Check-in Modal

```
┌──────────────────────────────────┐
│ 😊 오늘의 감정 체크인     [✕]  │
├──────────────────────────────────┤
│                                  │
│  오늘 기분이 어떤가요?          │
│                                  │
│  😄  🙂  😐  😢  😰           │
│  좋음 괜찮 보통 슬픔 불안       │
│                                  │
│  한줄 메모 (선택)               │
│  ┌──────────────────────────┐   │
│  │                          │   │
│  └──────────────────────────┘   │
│                                  │
│  📊 이번 주 감정 추이           │
│  [차트 영역]                    │
│                                  │
│  [기록하기]                     │
└──────────────────────────────────┘
```

### 4.5 User Flow

```
Landing Visit
  │
  ├── [무료로 시작하기] → Onboarding Flow
  │     ├── 목적 선택 (복수)
  │     ├── 간이 심리검사 (5문항)
  │     ├── 결과 + 맞춤 추천
  │     └── 첫 기능 체험 유도
  │
  ├── [Feature Card CTA] → 해당 Modal 열기
  │     ├── AI 상담 → Chat Modal
  │     ├── 심리검사 → Assessment Modal
  │     ├── 감정 체크인 → Mood Modal
  │     └── 전문 상담사 → Counselor Modal
  │
  └── [Scroll] → 섹션별 자연스러운 탐색
```

---

## 5. Data Model (LocalStorage)

### 5.1 Mood Records

```javascript
// localStorage key: "mindCounseling_moods"
[
  {
    id: "uuid",
    mood: "good",        // good | okay | neutral | sad | anxious
    emoji: "😄",
    note: "오늘 산책했더니 기분 좋음",
    timestamp: "2026-04-02T10:00:00Z"
  }
]
```

### 5.2 Assessment Results

```javascript
// localStorage key: "mindCounseling_assessments"
[
  {
    id: "uuid",
    type: "PHQ-9",       // PHQ-9 | GAD-7
    answers: [0, 1, 2, 1, 0, 1, 2, 0, 1],
    totalScore: 8,
    severity: "mild",    // minimal | mild | moderate | moderately-severe | severe
    timestamp: "2026-04-02T10:00:00Z"
  }
]
```

### 5.3 Chat History

```javascript
// localStorage key: "mindCounseling_chatHistory"
[
  {
    role: "assistant",   // assistant | user
    content: "안녕하세요! 오늘 기분이 어떠세요?",
    timestamp: "2026-04-02T10:00:00Z"
  }
]
```

---

## 6. Implementation Order

### Phase 1: Landing Page (Supanova)
1. [ ] index.html — Hero, Features, HowItWorks, Testimonials, Pricing, CTA, Footer
2. [ ] css/styles.css — 디자인 시스템, 컴포넌트 스타일
3. [ ] 반응형 디자인 (Mobile → Desktop)
4. [ ] 스크롤 애니메이션 (AOS.js)

### Phase 2: Interactive Features
5. [ ] js/app.js — 네비게이션, 모달 시스템, 라우팅
6. [ ] js/chat.js — AI 챗봇 UI + 시뮬레이션 응답
7. [ ] js/assessment.js — PHQ-9/GAD-7 설문 + 자동 채점
8. [ ] js/mood.js — 감정 체크인 + 차트 표시
9. [ ] js/community.js — 커뮤니티 UI

### Phase 3: Polish
10. [ ] 다크모드 토글
11. [ ] Lighthouse 최적화
12. [ ] 크로스 브라우저 테스트
13. [ ] GitHub Pages 배포

---

## 7. Security Considerations

- [x] 서버 없음 (LocalStorage만 사용) — 데이터 유출 위험 최소
- [x] 민감 데이터 고지: "데이터는 브라우저에만 저장됩니다" 안내
- [x] XSS 방지: innerHTML 대신 textContent 사용
- [x] AI 면책 조항: "전문 의료 상담을 대체하지 않습니다" 명시
- [x] 위기 안내: 자살예방상담전화 1393, 정신건강위기상담전화 1577-0199 표시

---

## 8. Test Plan

| # | 테스트 시나리오 | 예상 결과 | 플랫폼 |
|---|---------------|----------|--------|
| 1 | 랜딩 페이지 로드 | FCP < 1.5초, 모든 섹션 표시 | ALL |
| 2 | AI 챗봇 대화 | 메시지 입력 → 응답 표시 | ALL |
| 3 | PHQ-9 설문 완료 | 9문항 → 점수 계산 → 결과 표시 | ALL |
| 4 | GAD-7 설문 완료 | 7문항 → 점수 계산 → 결과 표시 | ALL |
| 5 | 감정 체크인 | 이모지 선택 → 메모 → 저장 → 차트 | ALL |
| 6 | 반응형 375px | 모든 섹션 정상 레이아웃 | Mobile |
| 7 | 반응형 1440px | 모든 섹션 정상 레이아웃 | Desktop |
| 8 | 다크모드 토글 | 색상 전환, 가독성 유지 | ALL |

---

## Version History

| Version | Date | Changes | Author |
|---------|------|---------|--------|
| 0.1 | 2026-04-02 | 초안 작성 | kimminjae413 |
