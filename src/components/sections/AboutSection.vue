<template>
  <section id="about" class="about" data-theme="dark">
    <div class="container">
      <div class="about-header reveal">
        <span class="about-badge">About</span>
        <h2 class="about-title reveal delay-1">
          A creative designer with over 20 years of experience<br>
          in web design and web production.
        </h2>
        <p class="about-desc reveal delay-2">
          Conveying brand stories through visual language,<br>
          creating meaningful connections between users and content.
        </p>
      </div>

      <!-- 3-card row -->
      <div class="about-cards">
        <div
          v-for="(card, i) in cards"
          :key="i"
          class="about-card"
          :class="{ 'is-active': activeIndex === i }"
          @click="goToCard(i)"
        >
          <div class="about-card__inner">
            <!-- Card 1: Balance — 마름모 -->
            <svg v-if="i === 0" viewBox="-5 -5 210 210" fill="none" xmlns="http://www.w3.org/2000/svg" class="card-svg">
              <!-- 중앙 큰 마름모 -->
              <polygon points="100,38 162,100 100,162 38,100" stroke="rgba(255,255,255,0.75)" stroke-width="1.5"/>
              <!-- 상 r=9 -->
              <polygon points="100,9 109,18 100,27 91,18" stroke="rgba(255,255,255,0.55)" stroke-width="1"/>
              <!-- 상 r=12 -->
              <polygon points="100,6 112,18 100,30 88,18" stroke="rgba(255,255,255,0.28)" stroke-width="1"/>
              <!-- 상 r=20 -->
              <polygon points="100,-2 120,18 100,38 80,18" stroke="rgba(255,255,255,0.12)" stroke-width="1"/>
              <!-- 우 r=9 -->
              <polygon points="182,91 191,100 182,109 173,100" stroke="rgba(255,255,255,0.55)" stroke-width="1"/>
              <!-- 우 r=12 -->
              <polygon points="182,88 194,100 182,112 170,100" stroke="rgba(255,255,255,0.28)" stroke-width="1"/>
              <!-- 우 r=20 -->
              <polygon points="182,80 202,100 182,120 162,100" stroke="rgba(255,255,255,0.12)" stroke-width="1"/>
              <!-- 하 r=9 -->
              <polygon points="100,173 109,182 100,191 91,182" stroke="rgba(255,255,255,0.55)" stroke-width="1"/>
              <!-- 하 r=12 -->
              <polygon points="100,170 112,182 100,194 88,182" stroke="rgba(255,255,255,0.28)" stroke-width="1"/>
              <!-- 하 r=20 -->
              <polygon points="100,162 120,182 100,202 80,182" stroke="rgba(255,255,255,0.12)" stroke-width="1"/>
              <!-- 좌 r=9 -->
              <polygon points="18,91 27,100 18,109 9,100" stroke="rgba(255,255,255,0.55)" stroke-width="1"/>
              <!-- 좌 r=12 -->
              <polygon points="18,88 30,100 18,112 6,100" stroke="rgba(255,255,255,0.28)" stroke-width="1"/>
              <!-- 좌 r=20 -->
              <polygon points="18,80 38,100 18,120 -2,100" stroke="rgba(255,255,255,0.12)" stroke-width="1"/>
              <!-- 우상 (r=9) -->
              <polygon points="142,49 151,58 142,67 133,58" stroke="rgba(255,255,255,0.35)" stroke-width="1"/>
              <!-- 우상 (r=12) -->
              <polygon points="142,46 154,58 142,70 130,58" stroke="rgba(255,255,255,0.2)" stroke-width="1"/>
              <!-- 우상 (r=15) -->
              <polygon points="142,43 157,58 142,73 127,58" stroke="rgba(255,255,255,0.1)" stroke-width="1"/>
              <!-- 우하 (r=9) -->
              <polygon points="142,133 151,142 142,151 133,142" stroke="rgba(255,255,255,0.35)" stroke-width="1"/>
              <!-- 우하 (r=12) -->
              <polygon points="142,130 154,142 142,154 130,142" stroke="rgba(255,255,255,0.2)" stroke-width="1"/>
              <!-- 우하 (r=15) -->
              <polygon points="142,127 157,142 142,157 127,142" stroke="rgba(255,255,255,0.1)" stroke-width="1"/>
              <!-- 좌하 (r=9) -->
              <polygon points="58,133 67,142 58,151 49,142" stroke="rgba(255,255,255,0.35)" stroke-width="1"/>
              <!-- 좌하 (r=12) -->
              <polygon points="58,130 70,142 58,154 46,142" stroke="rgba(255,255,255,0.2)" stroke-width="1"/>
              <!-- 좌하 (r=15) -->
              <polygon points="58,127 73,142 58,157 43,142" stroke="rgba(255,255,255,0.1)" stroke-width="1"/>
              <!-- 좌상 (r=9) -->
              <polygon points="58,49 67,58 58,67 49,58" stroke="rgba(255,255,255,0.35)" stroke-width="1"/>
              <!-- 좌상 (r=12) -->
              <polygon points="58,46 70,58 58,70 46,58" stroke="rgba(255,255,255,0.2)" stroke-width="1"/>
              <!-- 좌상 (r=15) -->
              <polygon points="58,43 73,58 58,73 43,58" stroke="rgba(255,255,255,0.1)" stroke-width="1"/>
            </svg>

            <!-- Card 2: Harmony — 곡선 + 직선 -->
            <svg v-if="i === 1" viewBox="0 0 200 200" fill="none" xmlns="http://www.w3.org/2000/svg" class="card-svg">
              <!-- 큰 곡선 아치 -->
              <path d="M 20 175 Q 100 18 180 175" stroke="rgba(255,255,255,0.72)" stroke-width="1.5"/>
              <!-- 내부 중간 곡선 -->
              <path d="M 48 175 Q 100 68 152 175" stroke="rgba(255,255,255,0.45)" stroke-width="1"/>
              <!-- 작은 곡선 -->
              <path d="M 76 175 Q 100 120 124 175" stroke="rgba(255,255,255,0.28)" stroke-width="1"/>
              <!-- 수평 직선들 -->
              <line x1="20" y1="100" x2="180" y2="100" stroke="rgba(255,255,255,0.35)" stroke-width="1"/>
              <line x1="20" y1="130" x2="180" y2="130" stroke="rgba(255,255,255,0.2)" stroke-width="1"/>
              <!-- 사선 -->
              <line x1="20" y1="40" x2="180" y2="175" stroke="rgba(255,255,255,0.22)" stroke-width="1"/>
              <!-- 수직 직선 -->
              <line x1="100" y1="20" x2="100" y2="180" stroke="rgba(255,255,255,0.18)" stroke-width="1" stroke-dasharray="4 4"/>
            </svg>

            <!-- Card 3: Imagination — 달팽이 원형들 -->
            <svg v-if="i === 2" viewBox="0 0 200 200" fill="none" xmlns="http://www.w3.org/2000/svg" class="card-svg">
              <!-- 피보나치 원 배열 -->
              <circle cx="108" cy="112" r="62" stroke="rgba(255,255,255,0.7)" stroke-width="1.5"/>
              <circle cx="70"  cy="70"  r="38" stroke="rgba(255,255,255,0.52)" stroke-width="1.2"/>
              <circle cx="140" cy="52"  r="22" stroke="rgba(255,255,255,0.4)" stroke-width="1"/>
              <circle cx="160" cy="148" r="14" stroke="rgba(255,255,255,0.32)" stroke-width="1"/>
              <circle cx="44"  cy="148" r="9"  stroke="rgba(255,255,255,0.25)" stroke-width="1"/>
              <circle cx="160" cy="90"  r="6"  stroke="rgba(255,255,255,0.2)" stroke-width="1"/>
              <circle cx="112" cy="22"  r="4"  stroke="rgba(255,255,255,0.18)" stroke-width="1"/>
            </svg>
          </div>

          <p class="about-card__title">{{ card.title }}</p>
        </div>
      </div>

      <!-- 점 네비게이션 -->
      <div class="about-dots" role="tablist" aria-label="슬라이드 선택">
        <button
          v-for="(card, i) in cards"
          :key="i"
          class="about-dot"
          :class="{ 'is-active': activeIndex === i }"
          @click="goToCard(i)"
          :aria-label="`${i + 1}번 슬라이드`"
          role="tab"
          :aria-selected="activeIndex === i"
        ></button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const activeIndex = ref(1)

const cards = [
  { title: 'Balance' },
  { title: 'Harmony' },
  { title: 'Imagination' },
]

let autoTimer = null
let resumeTimer = null

function goToCard(index) {
  activeIndex.value = index
  stopAuto()
  resumeTimer = setTimeout(startAuto, 4000)
}

function startAuto() {
  autoTimer = setInterval(() => {
    activeIndex.value = (activeIndex.value + 1) % cards.length
  }, 3000)
}

function stopAuto() {
  clearInterval(autoTimer)
  clearTimeout(resumeTimer)
  autoTimer = null
}

onMounted(() => startAuto())
onUnmounted(() => stopAuto())
</script>

<style scoped>
@import '../../style/about.css';
</style>
