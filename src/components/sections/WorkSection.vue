<template>
  <section id="work" class="section work" data-theme="dark">
    <div class="container">

      <!-- 헤더 -->
      <div class="work-header reveal">
        <span class="work-badge">Work</span>
        <h2 class="work-title reveal delay-1">
          Trusted by enterprise, finance,<br>and public sector clients.
        </h2>
        <p class="work-desc reveal delay-2">
          A foundation of diverse, high-stakes projects — translated into design<br>
          and web publishing that meets the highest standards.
        </p>
      </div>

      <!-- 가로 점선 타임라인 -->
      <div class="work-timeline reveal delay-3">
        <div class="work-timeline__line"></div>
        <button
          v-for="cat in categories"
          :key="cat.key"
          class="work-timeline__node"
          @click="openOverlay(cat.key)"
          :aria-label="`${cat.label} 수행이력 보기`"
        >
          <span class="node-dot"></span>
          <span class="node-label">{{ cat.label }}</span>
          <span class="node-count">{{ countByCategory(cat.key) }}</span>
        </button>
      </div>

    </div>
  </section>

  <!-- 팝업 오버레이 -->
  <Teleport to="body">
    <transition name="slide-up">
      <div v-if="selectedBox" class="work-overlay" role="dialog" aria-modal="true">

        <div class="overlay-header">
          <div class="overlay-meta">
            <span class="overlay-badge">Work</span>
            <span class="overlay-divider">·</span>
            <h2 class="overlay-title">{{ activeCategory?.label }}</h2>
            <span class="overlay-count">{{ overlayWorks.length }}건</span>
          </div>
          <button class="overlay-close" @click="closeOverlay" aria-label="닫기">
            <svg width="18" height="18" viewBox="0 0 18 18" fill="none">
              <line x1="2" y1="2" x2="16" y2="16" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
              <line x1="16" y1="2" x2="2" y2="16" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
            </svg>
          </button>
        </div>

        <div class="overlay-body">
          <div class="overlay-container">
            <div class="timeline">
              <div v-for="(item, idx) in overlayWorks" :key="idx" class="timeline-item">
                <div class="timeline-left">
                  <span class="timeline-year">
                    {{ item.year }}<template v-if="item.yearEnd">–{{ item.yearEnd }}</template>
                  </span>
                  <span class="timeline-period">{{ item.period }}</span>
                </div>
                <div class="timeline-line">
                  <div class="timeline-dot"></div>
                </div>
                <div class="timeline-right">
                  <div class="timeline-card">
                    <span class="card-period-mobile">{{ item.year }} · {{ item.period }}</span>
                    <div class="card-header">
                      <h3 class="card-title">{{ item.title }}</h3>
                      <span class="card-client">{{ item.client }}</span>
                    </div>
                    <span class="card-role">{{ item.role }}</span>
                    <p class="card-desc">{{ item.description }}</p>
                    <ul class="card-tags">
                      <li v-for="tag in item.tags" :key="tag" class="tag">{{ tag }}</li>
                    </ul>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

      </div>
    </transition>
  </Teleport>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'

const categories = [
  { key: 'enterprise', label: '대기업' },
  { key: 'finance',    label: '금융' },
  { key: 'public',     label: '공공기관' },
  { key: 'others',     label: '기타' },
]

const works = [
  // ── 대기업 (Samsung + SK) ─────────────────────────────────────────
  { category: 'enterprise', year: '2025', yearEnd: '2026', period: '2025.06 — 2026.04', title: '삼성전자 ERP 사업', client: '삼성전자', role: 'Designer / Publisher', description: '랜딩 화면 및 서브 작업 화면 웹디자인. Vue.js 환경 퍼블리싱 작업.', tags: ['Vue.js', 'SCSS', 'Web Design', 'Lego'] },
  { category: 'enterprise', year: '2024', period: '2024.03 — 2024.12', title: '수요포탈 CRM 이관 작업', client: '삼성디스플레이', role: 'Designer / Publisher', description: '수요포탈 내 CRM 적용 및 관리자 화면·검색 화면·Tableau 전환 작업.', tags: ['Vue.js', 'SCSS', 'Tableau', 'Lego'] },
  { category: 'enterprise', year: '2023', period: '2023.06 — 2023.11', title: 'SK C&C College 교육 포털', client: 'SK C&C', role: 'Publisher', description: 'SK C&C 교육 포털사이트 퍼블리싱 작업.', tags: ['Figma', 'Visual Studio Code'] },
  { category: 'enterprise', year: '2020', period: '2020.09 — 2020.12', title: '삼성SDS 보안 솔루션 (SSIS·넥스사인)', client: '삼성에스디에스', role: 'Designer / Publisher', description: 'SSIS 메인·서브·로그인 페이지 디자인. 넥스사인 모바일 디자인.', tags: ['XD', 'Zeplin', 'Mobile Design'] },
  { category: 'enterprise', year: '2013', yearEnd: '2015', period: '2013.12 — 2015.03', title: '삼성서울병원 SMC 차세대 시스템', client: '삼성서울병원', role: 'Web Designer', description: 'EMR 화면 디자인 및 전체 디자인 관리. UX/UI 디자인 총괄.', tags: ['UX/UI Design', 'EMR', 'Photoshop'] },
  { category: 'enterprise', year: '2012', yearEnd: '2013', period: '2012.08 — 2013.03', title: '삼성전자 SEC Learning Platform 구축', client: '삼성전자', role: 'Designer / Publisher', description: 'SCAI 신규사이트 전체 디자인 및 관리자 웹표준 코딩. myCoach 리뉴얼.', tags: ['Web Standard', 'HTML/CSS', 'Photoshop'] },
  { category: 'enterprise', year: '2011', period: '2011.08 — 2011.09', title: 'SK T-이러닝', client: 'SK텔레콤', role: 'Publisher (Mobile)', description: '갤럭시탭 10.1 HTML5 웹표준 작업.', tags: ['HTML5', 'Web Standard', 'Mobile'] },
  { category: 'enterprise', year: '2011', period: '2011.06 — 2011.06', title: '삼성전자 PVI 고도화 프로젝트', client: '삼성전자', role: 'Designer / Publisher', description: '퍼블리싱, 웹디자인 및 웹표준 작업.', tags: ['Web Standard', 'HTML/CSS'] },
  { category: 'enterprise', year: '2003', yearEnd: '2004', period: '2003.10 — 2004.12', title: '삼성전자 연구소', client: '삼성전자', role: 'Web Designer', description: '연구소 내 각 파트 웹디자인 및 아이콘 작업.', tags: ['Web Design', 'Illustrator', 'Photoshop'] },
  { category: 'enterprise', year: '2002', period: '2002.07 — 2002.11', title: 'SK 팅·TTL·모네타', client: 'SK (티월드)', role: 'Web Designer', description: '메일링 디자인 및 사이트 내 추가 디자인.', tags: ['Web Design', 'Photoshop'] },
  { category: 'enterprise', year: '2002', period: '2002.01 — 2002.04', title: 'SK Academy 포털 구축', client: 'SK', role: 'Web Designer', description: 'SK Academy 포털사이트 구축 디자인.', tags: ['Web Design', 'Photoshop'] },
  { category: 'enterprise', year: '2001', period: '2001.11 — 2001.12', title: 'SK 본사 유지보수', client: 'SK', role: 'Web Designer', description: 'SK 본사 내 사이트 유지보수.', tags: ['Web Design'] },
  { category: 'enterprise', year: '2001', period: '2001.09 — 2001.10', title: 'SK CEO 홈페이지 개편', client: 'SK', role: 'Web Designer', description: 'SK 김승정 회장 홈페이지 개편 디자인.', tags: ['Web Design', 'Photoshop'] },
  { category: 'enterprise', year: '2001', period: '2001.06 — 2001.08', title: 'SK 글로벌 사이트', client: 'SK 글로벌', role: 'Web Designer', description: 'SK 글로벌 사이트 디자인 유지보수.', tags: ['Web Design'] },
  { category: 'enterprise', year: '2001', period: '2001.01 — 2001.05', title: 'SK France 사이트', client: 'SK 글로벌', role: 'Web Designer', description: 'SK 글로벌 내 프랑스 사이트 디자인.', tags: ['Web Design', 'Flash'] },
  { category: 'enterprise', year: '2000', period: '2000.11 — 2000.12', title: 'SK Footwear', client: 'SK 글로벌', role: 'Web Designer', description: '사이트 디자인 및 HTML 작업.', tags: ['Web Design', 'HTML'] },
  { category: 'enterprise', year: '2000', period: '2000.08 — 2000.10', title: 'SK D-TEG 제품 사이트', client: 'SK 글로벌', role: 'Web Designer', description: 'SK 글로벌 내 제품 사이트 디자인.', tags: ['Web Design', 'Photoshop'] },

  // ── 금융 ─────────────────────────────────────────────────────────
  { category: 'finance', year: '2022', yearEnd: '2023', period: '2022.11 — 2023.03', title: 'KB손해보험 UIUX 전환', client: 'KB손해보험', role: 'Publisher', description: 'xplatform·trustform → 웹스퀘어 전환 작업 및 공통 작업.', tags: ['웹스퀘어', 'UIUX'] },
  { category: 'finance', year: '2021', yearEnd: '2022', period: '2021.05 — 2022.02', title: '신한은행 마이데이터', client: '신한은행', role: 'Publisher (Mobile)', description: '신한은행 마이데이터 모바일(하이브리드) 퍼블리싱.', tags: ['HTML5', 'CSS3', 'Mobile', 'Sketch'] },
  { category: 'finance', year: '2015', period: '2015.09 — 2015.11', title: 'PCA생명 모바일', client: 'PCA생명', role: 'Publisher (Mobile)', description: 'PCA생명 모바일 작업. HTML5·CSS3.', tags: ['HTML5', 'CSS3', 'Mobile'] },
  { category: 'finance', year: '2011', yearEnd: '2012', period: '2011.12 — 2012.02', title: "신한생명 모바일 Big-Dream's", client: '신한생명', role: 'Publisher', description: 'HTML5·CSS3 기반 아이패드·갤럭시탭·안드로이드 모바일 퍼블리싱.', tags: ['HTML5', 'CSS3', 'Mobile'] },

  // ── 공공기관 ──────────────────────────────────────────────────────
  { category: 'public', year: '2015', period: '2015.05 — 2015.06', title: '한국도로공사 EA 고도화 2차', client: '한국도로공사', role: 'Publisher / Web Designer', description: '한국도로공사 내부시스템 디자인 및 퍼블리싱.', tags: ['DreamWeaver', 'Photoshop'] },
  { category: 'public', year: '2013', period: '2013.06 — 2013.09', title: '한국무역정보통신 전자증지 서비스', client: '한국무역정보통신', role: 'Publisher / Web Designer', description: '퍼블리싱, 웹디자인, 웹표준, 웹접근성 작업.', tags: ['Web Standard', 'Accessibility'] },
  { category: 'public', year: '2012', period: '2012.03 — 2012.04', title: '당진시청 문화관광 사이트', client: '당진시', role: 'Publisher / Web Designer', description: '모바일 퍼블리싱, 웹디자인, 웹표준 작업.', tags: ['Mobile', 'Web Standard'] },
  { category: 'public', year: '2011', period: '2011.11', title: 'NHRD 홈페이지', client: '한국직업능력개발원', role: 'Publisher / Web Designer', description: '퍼블리싱, 웹표준, 웹접근성 작업 및 디자인 관리.', tags: ['Web Standard', 'Accessibility'] },
  { category: 'public', year: '2010', period: '2010.05 — 2010.06', title: '서울의료관광 사이트', client: '서울의료관광', role: 'Publisher / Web Designer', description: '한·중·일·영 4개국어 퍼블리싱·디자인·웹표준·웹접근성 작업.', tags: ['Web Standard', 'Accessibility', 'Multi-language'] },
  { category: 'public', year: '2009', period: '2009.07 — 2009.12', title: '건강증진사업지원단', client: '건강증진사업지원단', role: 'Publisher / Web Designer', description: '6개 사이트 디자인 총괄, 웹표준·웹접근성 작업.', tags: ['Web Standard', 'Accessibility'] },
  { category: 'public', year: '2006', yearEnd: '2007', period: '2006.10 — 2007.07', title: '파주시청 인트라넷·온라인 개발', client: '파주시청', role: 'Publisher / Web Designer', description: '인트라넷 11개·온라인 2개 사이트 개발.', tags: ['HTML', 'CSS', 'Flash'] },

  // ── 기타 ─────────────────────────────────────────────────────────
  { category: 'others', year: '2022', period: '2022.05 — 2022.09', title: '서브원 이커머스', client: '서브원', role: 'Publisher', description: '모바일·PC HTML5·CSS3 퍼블리싱.', tags: ['HTML5', 'CSS3', 'XD', 'GitHub'] },
  { category: 'others', year: '2018', period: '2018.03 — 2018.08', title: '연세대학교의료원 ALYND', client: '연세세브란스병원', role: 'Publisher / Web Designer', description: '연세대학교의료원 내 사이트 퍼블리싱 및 웹디자인.', tags: ['DreamWeaver', 'Photoshop'] },
  { category: 'others', year: '2012', period: '2012.04 — 2012.08', title: 'KT 올레샵 운영', client: 'KT', role: 'Web Designer', description: 'KT 올레샵 운영 웹디자인.', tags: ['Web Design', 'Photoshop'] },
  { category: 'others', year: '2011', period: '2011.07', title: '부뷕 쇼핑몰 매거진', client: '비즈엠피플', role: 'Web Designer', description: '쇼핑몰 사이트 내 매거진 사이트 디자인.', tags: ['Web Design', 'Photoshop'] },
  { category: 'others', year: '2011', period: '2011.03 — 2011.05', title: '네오위즈 구매시스템', client: '네오위즈', role: 'Publisher / Web Designer', description: '구매시스템 디자인 및 CSS·웹표준 작업.', tags: ['CSS', 'Web Standard'] },
  { category: 'others', year: '2011', period: '2011.01 — 2011.02', title: 'GS리테일 MMK 프로젝트', client: 'GS리테일', role: 'Web Designer', description: 'GS리테일 키오스크 디자인 및 사이트 디자인 수정.', tags: ['Web Design', 'Photoshop'] },
  { category: 'others', year: '2010', period: '2010.08 — 2010.09', title: '트라일러앤컴퍼니 사내교육', client: '아코바㈜', role: 'Web Designer', description: '사내 교육 사이트 디자인.', tags: ['Web Design', 'DreamWeaver'] },
  { category: 'others', year: '2009', period: '2009.04 — 2009.06', title: '자스텍 자동차부품 웹포탈', client: '자스텍', role: 'Publisher / Web Designer', description: '웹포탈 사이트 디자인 및 웹표준 작업.', tags: ['Web Standard', 'Flash'] },
  { category: 'others', year: '2007', yearEnd: '2008', period: '2007.11 — 2008.10', title: '대한축구협회 각 구단 사이트', client: '대한축구협회', role: 'Web Designer', description: '각 축구구단 사이트 리뉴얼 및 유지보수.', tags: ['Web Design', 'Photoshop'] },
  { category: 'others', year: '2005', yearEnd: '2006', period: '2005.10 — 2006.01', title: '솔트케이크 홈페이지', client: '솔트케이크', role: 'Web Designer', description: '사이트 전체 관리 및 디자인.', tags: ['Web Design', 'Flash'] },
  { category: 'others', year: '2005', period: '2005.03 — 2005.09', title: '문화진흥원 포털사이트', client: '문화진흥원', role: 'Web Designer / PM', description: '사이트 전체 PM 및 웹디자인 작업.', tags: ['Web Design', 'PM', 'Flash'] },
  { category: 'others', year: '2002', yearEnd: '2003', period: '2002.12 — 2003.02', title: '두산 와인사이트', client: '두산', role: 'Web Designer', description: '두산 와인 사이트 유지보수.', tags: ['Web Design', 'Photoshop'] },
]

const selectedBox = ref(null)

const activeCategory = computed(() =>
  categories.find(c => c.key === selectedBox.value)
)

const overlayWorks = computed(() =>
  selectedBox.value
    ? works.filter(w => w.category === selectedBox.value).sort((a, b) => Number(b.year) - Number(a.year))
    : []
)

function countByCategory(key) {
  return works.filter(w => w.category === key).length
}

function openOverlay(key) {
  const sw = window.innerWidth - document.documentElement.clientWidth
  document.body.style.paddingRight = sw + 'px'
  document.body.style.overflow = 'hidden'
  selectedBox.value = key
}

function closeOverlay() {
  selectedBox.value = null
  document.body.style.overflow = ''
  document.body.style.paddingRight = ''
}

function onKeydown(e) {
  if (e.key === 'Escape') closeOverlay()
}

onMounted(() => window.addEventListener('keydown', onKeydown))
onUnmounted(() => {
  window.removeEventListener('keydown', onKeydown)
  document.body.style.overflow = ''
})
</script>

<style scoped>
@import '../../style/work.css';
</style>
