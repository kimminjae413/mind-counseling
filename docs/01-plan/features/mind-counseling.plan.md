# 심리상담 웹서비스 (Mind Counseling) Planning Document

> **Summary**: AI 기반 한국형 온라인 심리상담 플랫폼 — 감정 체크인, AI 챗봇 상담, 전문 상담사 매칭, 심리검사, 커뮤니티 기능 제공
>
> **Project**: mind-counseling
> **Version**: 1.0.0
> **Author**: kimminjae413
> **Date**: 2026-04-02
> **Status**: Draft

---

## 1. Overview

### 1.1 Purpose

MZ세대를 중심으로 급증하는 멘탈헬스 수요에 대응하여, **접근성 높은 온라인 심리상담 플랫폼**을 구축한다. AI 기반 일상 관리와 전문 상담사 연결을 결합한 **하이브리드 모델**로, 가벼운 마음 관리부터 전문 상담까지 원스톱으로 제공한다.

### 1.2 Background

- **시장 현황**: 한국 디지털 멘탈헬스 시장 3,000~5,000억 원 규모, 연평균 20~30% 성장
- **수요 변화**: 코로나 이후 정신건강 진료 22% 증가, 20~30대 우울·불안 진료 30~40% 급증
- **인식 변화**: MZ세대 심리상담 낙인(stigma) 빠르게 감소, "마음 관리 = 자기계발" 인식 확산
- **시장 기회**: 뚜렷한 1위 사업자 없는 분절된 시장 → 선점 기회 존재
- **기술 트렌드**: AI + 인간 하이브리드 상담 모델이 글로벌 표준으로 수렴 중

### 1.3 Related Documents

- 시장 리서치: 별도 리서치 보고서 (2026-04-02)
- 경쟁사 분석: 트로스트, 마인드카페, BetterHelp, Woebot 등 10+ 서비스 분석 완료

---

## 2. Scope

### 2.1 In Scope (MVP - Phase 1)

- [x] **랜딩 페이지**: 서비스 소개, 가치 제안, CTA
- [x] **감정 체크인**: 오늘의 기분 기록 (이모지 기반)
- [x] **AI 챗봇 상담**: GPT 기반 대화형 심리 지원 (UI 시뮬레이션)
- [x] **심리검사**: PHQ-9(우울), GAD-7(불안) 자가진단
- [x] **상담사 프로필**: 전문 상담사 소개 및 매칭 UI
- [x] **커뮤니티**: 익명 고민 나눔 게시판 UI
- [x] **온보딩 플로우**: 단계별 사용자 등록 UI
- [x] **반응형 디자인**: 모바일/태블릿/데스크톱 대응

### 2.2 Out of Scope (향후 확장)

- 실제 백엔드 서버 / 데이터베이스 연동
- 결제 시스템 (구독/건당 과금)
- 실시간 화상/음성 상담 (WebRTC)
- B2B 기업 복지 대시보드
- 보험 연계 시스템
- 네이티브 모바일 앱 (React Native/Flutter)

---

## 3. Requirements

### 3.1 Functional Requirements

| ID | Requirement | Priority | Status |
|----|-------------|----------|--------|
| FR-01 | 랜딩 페이지 — 서비스 소개, 핵심 가치, 사용 후기, CTA 버튼 | High | Pending |
| FR-02 | 감정 체크인 — 이모지 선택 + 한줄 메모로 오늘의 감정 기록 | High | Pending |
| FR-03 | AI 챗봇 — 대화형 인터페이스, 공감적 응답, 위기 감지 안내 | High | Pending |
| FR-04 | 심리검사 — PHQ-9/GAD-7 설문, 자동 채점, 결과 시각화 | High | Pending |
| FR-05 | 상담사 매칭 — 프로필 카드, 전문분야/경력/후기 표시, 예약 CTA | Medium | Pending |
| FR-06 | 커뮤니티 — 익명 게시판, 카테고리별 분류, 공감 버튼 | Medium | Pending |
| FR-07 | 온보딩 — 목적 파악 → 간이 검사 → 맞춤 추천 흐름 | Medium | Pending |
| FR-08 | 네비게이션 — 헤더/푸터, 섹션 간 스무스 스크롤 | High | Pending |
| FR-09 | 다크모드 지원 — 토글 스위치, 시스템 설정 연동 | Low | Pending |
| FR-10 | 반응형 디자인 — 모바일 375px ~ 데스크톱 1440px+ 대응 | High | Pending |

### 3.2 Non-Functional Requirements

| Category | Criteria | Measurement Method |
|----------|----------|-------------------|
| Performance | FCP < 1.5초, LCP < 2.5초 | Lighthouse |
| Accessibility | WCAG 2.1 AA 준수 | axe DevTools |
| SEO | Lighthouse SEO 90+ | Lighthouse |
| Browser | Chrome, Safari, Firefox, Edge 최신 2버전 | Manual Testing |
| Mobile | iOS Safari, Android Chrome 대응 | Responsive Testing |

---

## 4. Target Users

### 4.1 Primary Persona

| 항목 | 내용 |
|------|------|
| **이름** | 김지은 (가상) |
| **나이** | 28세 |
| **직업** | IT 스타트업 마케터 |
| **상황** | 업무 스트레스 + 대인관계 고민, 상담 경험 없음 |
| **니즈** | 가볍게 시작할 수 있는 마음 관리, 익명성 보장 |
| **행동** | 모바일 우선, SNS 활발, 자기계발 콘텐츠 소비 |
| **Pain Point** | 대면 상담은 부담스럽고, 어디서 시작할지 모름 |

### 4.2 Secondary Persona

| 항목 | 내용 |
|------|------|
| **이름** | 이준호 (가상) |
| **나이** | 35세 |
| **직업** | 중견기업 개발자 |
| **상황** | 번아웃, 수면 장애, 이전 상담 경험 있음 |
| **니즈** | 정기적 전문 상담 + 일상 감정 관리 도구 |
| **행동** | 효율 중시, 데이터 기반 자기 분석 선호 |
| **Pain Point** | 기존 앱은 너무 가볍거나 접근성이 떨어짐 |

---

## 5. Service Concept & Positioning

### 5.1 핵심 가치 제안 (Value Proposition)

> **"마음도 관리가 필요하니까"**
>
> 일상의 작은 감정부터 깊은 고민까지,
> AI와 전문 상담사가 함께하는 마음 관리 플랫폼

### 5.2 경쟁 포지셔닝

```
                    전문성 높음
                        ↑
                        |
          그리팅  ●     |     ● Mind Counseling
                        |       (AI + 전문상담 하이브리드)
       ─────────────────┼──────────────────→ 접근성 높음
                        |
          트로스트 ●    |     ● 마인드카페
                        |
                    전문성 낮음
```

### 5.3 차별화 전략

| 차별점 | 설명 |
|--------|------|
| **AI 하이브리드** | AI가 일상 관리 → 필요 시 전문 상담사 즉시 연결 |
| **데이터 기반 개인화** | 감정 일기 + 심리검사 데이터로 맞춤 콘텐츠/상담사 추천 |
| **프리미엄 UX** | 따뜻하고 안전한 느낌의 UI, Safe Space 디자인 |
| **과학적 근거** | PHQ-9, GAD-7 등 표준화된 검사 도구 활용 |

---

## 6. Revenue Model (향후 계획)

```
[무료 계층]
├── AI 챗봇 대화 (일 3회)
├── 감정 체크인 / 일기
├── 커뮤니티 열람
└── 간이 심리검사 1회

[베이직 구독] 월 9,900원
├── AI 챗봇 무제한
├── 프리미엄 콘텐츠
├── 감정 분석 리포트
└── 전문상담 할인 쿠폰 (월 1회)

[프로 구독] 월 49,900원
├── 베이직 전체 포함
├── 전문상담사 1:1 상담 (월 2회)
├── 화상/음성/채팅 선택
└── 상담 리포트 제공

[B2B 기업 복지]
├── 직원 1인당 월 5,000~15,000원
├── 관리자 대시보드 (익명 통계)
└── 맞춤 프로그램
```

---

## 7. Tech Stack & Architecture

### 7.1 Project Level Selection

| Level | Characteristics | Recommended For | Selected |
|-------|-----------------|-----------------|:--------:|
| **Starter** | Simple structure, HTML/CSS/JS | Static sites, landing pages | ✅ |
| Dynamic | Feature-based modules, BaaS | Web apps with backend | ☐ |
| Enterprise | Microservices, DI | High-traffic systems | ☐ |

### 7.2 Key Technical Decisions

| Decision | Selected | Rationale |
|----------|----------|-----------|
| Framework | Vanilla HTML/CSS/JS | Starter 레벨, GitHub Pages 배포에 최적 |
| Styling | Tailwind CSS (CDN) | 빠른 개발, 반응형 용이 |
| Animation | CSS Animations + AOS.js | 부드러운 마이크로 인터랙션 |
| Icons | Lucide Icons (CDN) | 가볍고 깔끔한 아이콘 |
| Font | Pretendard (한글) + Inter (영문) | 둥글고 부드러운 인상 |
| Deployment | GitHub Pages | 무료, 간편한 정적 호스팅 |
| AI Chat UI | 프론트엔드 시뮬레이션 | MVP 단계에서 백엔드 없이 체험 |

### 7.3 Folder Structure

```
mind-counseling/
├── index.html              # 메인 랜딩 + SPA 라우팅
├── css/
│   └── styles.css          # Tailwind 커스텀 + 컴포넌트 스타일
├── js/
│   ├── app.js              # 메인 앱 로직, 라우팅
│   ├── chat.js             # AI 챗봇 UI 로직
│   ├── assessment.js       # 심리검사 로직 (PHQ-9, GAD-7)
│   ├── mood.js             # 감정 체크인 로직
│   └── community.js        # 커뮤니티 UI 로직
├── assets/
│   ├── images/             # 일러스트, 아이콘
│   └── data/               # 상담사 프로필, 검사 문항 JSON
├── README.md
└── docs/                   # PDCA 문서
```

---

## 8. Design Direction

### 8.1 Color Palette

| Role | Color | Hex | Usage |
|------|-------|-----|-------|
| Primary | Sage Green | `#7BA68C` | 주요 CTA, 강조 |
| Secondary | Lavender | `#B8A9C9` | 보조 액센트 |
| Warm | Soft Peach | `#F5D5C8` | 배경 하이라이트 |
| Neutral | Off White | `#FAF9F6` | 배경 |
| Text | Charcoal | `#2D2D2D` | 본문 텍스트 |
| Muted | Warm Gray | `#8E8E8E` | 보조 텍스트 |

### 8.2 Tone & Manner

- **따뜻하고 공감적**: "~해야 한다" ❌ → "~해도 괜찮아요" ✅
- **안전한 공간**: 부드러운 모서리, 넉넉한 여백, 판단하지 않는 톤
- **과학적이면서 친근한**: 전문성은 유지하되 위압감 없이
- **일러스트 스타일**: 추상적·미니멀, 자연 요소 (나뭇잎, 물결, 하늘)

---

## 9. Page Structure (Sitemap)

```
🏠 Home (랜딩)
├── Hero Section — 핵심 메시지 + CTA
├── Features Section — 4가지 핵심 기능 소개
├── How It Works — 3단계 이용 방법
├── Testimonials — 사용 후기
├── Pricing — 요금제 안내
└── CTA Section — 최종 전환 유도

💬 AI 상담 (Chat)
├── 채팅 인터페이스
├── 감정 선택 프롬프트
└── 위기 시 전문상담 연결 안내

📋 심리검사 (Assessment)
├── 검사 선택 (PHQ-9 / GAD-7)
├── 설문 진행 (단계별)
└── 결과 대시보드 + 추천

😊 감정 체크인 (Mood)
├── 이모지 감정 선택
├── 한줄 메모
└── 감정 히스토리 (차트)

👤 상담사 (Counselors)
├── 상담사 목록 (필터링)
├── 프로필 상세
└── 예약 CTA

💬 커뮤니티 (Community)
├── 카테고리별 게시판
├── 글 상세 + 댓글
└── 공감 / 응원 버튼
```

---

## 10. Risks and Mitigation

| Risk | Impact | Likelihood | Mitigation |
|------|--------|------------|------------|
| AI 상담 윤리 이슈 — 자살/자해 위기 상황 | High | Medium | 위기 감지 시 전문 상담 전화(1393) 즉시 안내, 면책 조항 명시 |
| 개인정보 유출 — 민감 심리 데이터 | High | Low | MVP에서 서버 저장 없음(로컬 스토리지), 향후 AES-256 암호화 |
| 의료행위 오해 — "치료" 표현 사용 | Medium | Medium | "상담/관리" 용어만 사용, 의료 면책 고지 명시 |
| 상담사 자격 문제 — 무자격 상담 | High | Low | 자격증 검증 시스템 구축 (향후), MVP에서는 가상 프로필로 시연 |
| 사용자 리텐션 저하 | Medium | High | 감정 체크인 습관화, 알림 시스템, 커뮤니티 활성화 |

---

## 11. Success Criteria

### 11.1 Definition of Done (MVP)

- [ ] 랜딩 페이지 완성 (Hero, Features, HowItWorks, Testimonials, Pricing, CTA)
- [ ] AI 챗봇 UI 동작 (시뮬레이션 대화)
- [ ] 심리검사 2종 (PHQ-9, GAD-7) 완전 동작
- [ ] 감정 체크인 기능 동작 (로컬 스토리지 저장)
- [ ] 상담사 프로필 페이지 표시
- [ ] 커뮤니티 게시판 UI 표시
- [ ] 반응형 디자인 (Mobile/Tablet/Desktop)
- [ ] GitHub Pages 배포 완료

### 11.2 Quality Criteria

- [ ] Lighthouse Performance 90+
- [ ] Lighthouse Accessibility 90+
- [ ] Lighthouse SEO 90+
- [ ] 모바일 터치 타겟 44px 이상
- [ ] 크로스 브라우저 테스트 통과

---

## 12. Next Steps

1. [ ] Design 문서 작성 (`/pdca design mind-counseling`)
2. [ ] Supanova 스킬로 프리미엄 랜딩 페이지 디자인
3. [ ] 각 페이지/섹션 구현
4. [ ] Gap Analysis 및 품질 검증
5. [ ] GitHub Pages 배포

---

## Version History

| Version | Date | Changes | Author |
|---------|------|---------|--------|
| 0.1 | 2026-04-02 | 초안 작성 — 시장 리서치 기반 | kimminjae413 |
