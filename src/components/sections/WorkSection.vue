<template>
  <section id="work" class="section work">
    <div class="container">
      <div class="work-header">
        <span class="section-label">Experience</span>
        <h2 class="section-title">수행 이력</h2>
      </div>

      <div class="timeline">
        <div
          v-for="(item, index) in works"
          :key="index"
          class="timeline-item"
        >
          <div class="timeline-left">
            <span class="timeline-period">{{ item.period }}</span>
          </div>
          <div class="timeline-line">
            <div class="timeline-dot"></div>
          </div>
          <div class="timeline-right">
            <div class="timeline-card">
              <!-- 모바일에서는 카드 안에 날짜 표시 -->
              <span class="card-period-mobile">{{ item.period }}</span>
              <div class="card-header">
                <h3 class="card-title">{{ item.company }}</h3>
                <span class="card-role">{{ item.role }}</span>
              </div>
              <p class="card-desc">{{ item.description }}</p>
              <ul class="card-tags">
                <li v-for="tag in item.tags" :key="tag" class="tag">{{ tag }}</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const works = [
  {
    period: '2022 — 현재',
    company: '(주)크리에이티브스튜디오',
    role: 'Senior Designer',
    description: '브랜드 아이덴티티 설계 및 편집 디자인 리드. 주요 클라이언트의 비주얼 시스템을 구축하고 웹 퍼블리싱까지 원스톱으로 진행.',
    tags: ['Brand Identity', 'Editorial', 'Web Publishing'],
  },
  {
    period: '2019 — 2022',
    company: '디자인그룹 에이치',
    role: 'Designer',
    description: '광고 캠페인 및 온·오프라인 마케팅 콘텐츠 제작. 연간 100여 개 이상의 프로젝트를 담당하며 멀티 채널 비주얼 콘텐츠를 개발.',
    tags: ['Campaign', 'Print Design', 'Digital Contents'],
  },
  {
    period: '2017 — 2019',
    company: '(주)퍼블리시티랩',
    role: 'Web Publisher',
    description: 'HTML/CSS 기반 웹 퍼블리싱 및 반응형 UI 구현. 다수의 기업 웹사이트 구축 및 유지보수 담당.',
    tags: ['HTML/CSS', 'Responsive', 'UI Markup'],
  },
  {
    period: '2015 — 2017',
    company: '프리랜서',
    role: 'Freelance Designer',
    description: '스타트업 및 소상공인 대상 로고 디자인, 패키지 디자인, SNS 콘텐츠 제작. 다양한 산업군의 클라이언트와 협업.',
    tags: ['Logo', 'Package Design', 'SNS Contents'],
  },
]
</script>

<style scoped>
.work {
  background: var(--color-white);
}

.work-header {
  margin-bottom: 5rem;
}

/* 타임라인 */
.timeline {
  display: flex;
  flex-direction: column;
}

.timeline-item {
  display: grid;
  grid-template-columns: 180px 40px 1fr;
  align-items: stretch;
}

.timeline-left {
  padding: 2px 2rem 0 0;
  display: flex;
  align-items: flex-start;
}

.timeline-period {
  font-size: 0.8rem;
  font-weight: 500;
  color: var(--color-gray);
  letter-spacing: 0.05em;
  white-space: nowrap;
}

/* 타임라인 선 */
.timeline-line {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.timeline-line::before {
  content: '';
  position: absolute;
  top: 10px;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 1px;
  background: var(--color-gray-light);
}

.timeline-item:last-child .timeline-line::before {
  display: none;
}

.timeline-dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: var(--color-green);
  border: 2px solid var(--color-white);
  box-shadow: 0 0 0 1px var(--color-green);
  position: relative;
  z-index: 1;
  margin-top: 2px;
  flex-shrink: 0;
}

/* 카드 */
.timeline-right {
  padding: 0 0 3rem 2rem;
}

.timeline-card {
  padding: 1.75rem 2rem;
  border: 1px solid var(--color-gray-light);
  background: var(--color-white);
  border-radius: 20px 0 20px 0;
  transition: border-color var(--transition), box-shadow var(--transition);
}

.timeline-card:hover {
  border-color: var(--color-green);
  box-shadow: 0 8px 40px rgba(42, 122, 79, 0.06);
}

/* 모바일 전용 날짜 (데스크탑에서는 숨김) */
.card-period-mobile {
  display: none;
}

.card-header {
  display: flex;
  align-items: baseline;
  gap: 0.75rem;
  margin-bottom: 0.75rem;
  flex-wrap: wrap;
}

.card-title {
  font-family: var(--font-serif);
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--color-black);
}

.card-role {
  font-size: 0.8rem;
  font-weight: 500;
  color: var(--color-green);
  letter-spacing: 0.08em;
  white-space: nowrap;
}

.card-desc {
  font-size: 0.9rem;
  color: var(--color-gray);
  line-height: 1.8;
  margin-bottom: 1.25rem;
}

.card-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tag {
  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.08em;
  color: var(--color-green);
  background: var(--color-green-muted);
  padding: 0.25rem 0.75rem;
  border-radius: 2px;
}

/* ── 반응형 ── */
@media (max-width: 1024px) {
  .timeline-item {
    grid-template-columns: 140px 36px 1fr;
  }
}

@media (max-width: 768px) {
  .work-header {
    margin-bottom: 3rem;
  }
  .timeline-item {
    grid-template-columns: 28px 1fr;
  }
  .timeline-left {
    display: none;
  }
  .timeline-line {
    grid-column: 1;
  }
  .timeline-right {
    grid-column: 2;
    padding: 0 0 2rem 1.25rem;
  }
  .timeline-card {
    padding: 1.25rem 1.25rem;
  }
  /* 카드 안에 날짜 보여주기 */
  .card-period-mobile {
    display: block;
    font-size: 0.75rem;
    font-weight: 500;
    color: var(--color-gray);
    letter-spacing: 0.05em;
    margin-bottom: 0.6rem;
  }
  .card-title {
    font-size: 1.05rem;
  }
}

@media (max-width: 480px) {
  .timeline-right {
    padding: 0 0 1.75rem 1rem;
  }
  .timeline-card {
    padding: 1rem;
  }
}
</style>
