<template>
  <section id="portfolio" class="section portfolio">
    <div class="container">

      <!-- 헤더 -->
      <div class="portfolio-header reveal">
        <span class="portfolio-badge">Portfolio</span>
        <h2 class="portfolio-title reveal delay-1">Craft in Every Pixel.</h2>
        <p class="portfolio-desc reveal delay-2">
          Explore a range of projects where visual language and technical precision<br>
          come together to create meaningful web experiences.
        </p>
        <div class="swiper-nav reveal delay-3">
          <button class="nav-btn" @click="slideLeft" aria-label="이전">
            <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
              <path d="M13 16L7 10L13 4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </button>
          <button class="nav-btn" @click="slideRight" aria-label="다음">
            <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
              <path d="M7 16L13 10L7 4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </button>
        </div>
      </div>

    </div>

    <div class="swiper-outer">
      <div class="swiper-track" ref="trackRef">
        <div
          v-for="item in items"
          :key="item.id"
          class="swiper-slide"
          :class="{ 'is-active': activeId === item.id }"
          @click="onSlideClick(item)"
        >
          <div class="slide-thumb" :style="{ background: item.bg }">
            <div v-if="item.img" class="slide-img-wrap">
              <img :src="item.img" :alt="item.title" class="slide-img" :style="{ objectPosition: item.imgPos || 'center' }" />
            </div>

<div class="slide-info">
              <h3 class="slide-title">{{ item.title }}</h3>
              <p class="slide-year">{{ item.year }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- 팝업 -->
  <Teleport to="body">
    <Transition name="popup">
      <div v-if="popupItem" class="popup-overlay" @click.self="closePopup">
        <div class="popup-box">
          <button class="popup-close" @click="closePopup" aria-label="닫기">
            <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
              <path d="M15 5L5 15M5 5l10 10" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
            </svg>
          </button>
          <div class="popup-img-wrap" :style="{ background: popupItem.bg }">
            <img :src="popupItem.img" :alt="popupItem.title" class="popup-img" />
          </div>
          <div class="popup-meta">
            <p class="popup-year">{{ popupItem.year }}</p>
            <h3 class="popup-title">{{ popupItem.title }}</h3>
            <p v-if="popupItem.desc" class="popup-desc">{{ popupItem.desc }}</p>
          </div>
        </div>
      </div>
    </Transition>
  </Teleport>
</template>

<script setup>
import { ref, onMounted, onUnmounted, nextTick } from 'vue'

const items = [
  { id: 1, title: 'Integrated Business Platform', year: '2024', bg: '#ffffff', img: '/src/assets/Portfolio_01.png', imgPos: 'top', imgPad: '1rem', desc: '본 프로젝트는 기업 브랜드 컨셉을 기반으로 제작한 UI 디자인 시안입니다.\nAI 기반 이미지 생성 도구를 활용하여 컨셉 비주얼을 제작하였으며, 전체 레이아웃 및 UI 구성은 직접 기획하였습니다.' },
  { id: 2, title: 'Bio & Pharma',   year: '2023', bg: '#ffffff', img: '/src/assets/Portfolio_02.png', imgPos: 'top', imgPad: '1rem', desc: '본 프로젝트는 바이오, 제약 브랜드 컨셉을 기반으로 제작한 UI 디자인 시안입니다.\nAI 기반 이미지 생성 도구를 활용하여 컨셉 비주얼을 제작하였으며, 전체 레이아웃 및 UI 구성은 직접 기획하였습니다.' },
  { id: 3, title: 'Medical Clinic', year: '2022', bg: '#ffffff', img: '/src/assets/Portfolio_03.png', imgPos: 'top', imgPad: '1rem', desc: '본 프로젝트는 피부과 브랜드 컨셉을 기반으로 제작한 UI 디자인 시안입니다.\nAI 기반 이미지 생성 도구를 활용하여 컨셉 비주얼을 제작하였으며, 전체 레이아웃 및 UI 구성은 직접 기획하였습니다.' },
  { id: 4, title: 'Financial',  year: '2022', bg: '#ffffff', img: '/src/assets/Portfolio_04.png', imgPos: 'top', imgPad: '1rem', desc: '본 프로젝트는 금융 브랜드 컨셉을 기반으로 제작한 UI 디자인 시안입니다.\nAI 기반 이미지 생성 도구를 활용하여 컨셉 비주얼을 제작하였으며, 전체 레이아웃 및 UI 구성은 직접 기획하였습니다.' },
]

const activeId  = ref(null)
const popupItem = ref(null)
const trackRef  = ref(null)

function onSlideClick(item) {
  activeId.value = item.id
  if (item.img) popupItem.value = item
}

function closePopup() {
  popupItem.value = null
}

function onKeydown(e) {
  if (e.key === 'Escape') closePopup()
}

onMounted(() => {
  nextTick(() => { if (trackRef.value) trackRef.value.scrollLeft = 0 })
  window.addEventListener('keydown', onKeydown)
})
onUnmounted(() => window.removeEventListener('keydown', onKeydown))

function getStepWidth() {
  const slide = trackRef.value?.querySelector('.swiper-slide')
  if (!slide) return 300
  const gap = parseFloat(getComputedStyle(trackRef.value).columnGap) || 16
  return slide.offsetWidth + gap
}

function slideLeft()  { trackRef.value?.scrollBy({ left: -getStepWidth(), behavior: 'smooth' }) }
function slideRight() { trackRef.value?.scrollBy({ left:  getStepWidth(), behavior: 'smooth' }) }
</script>

<style scoped>
@import '../../style/portfolio.css';
</style>
