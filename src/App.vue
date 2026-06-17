<script setup>
import { onMounted, nextTick } from 'vue'
import AppHeader from './components/layout/AppHeader.vue'
import AppFooter from './components/layout/AppFooter.vue'
import HeroSection from './components/sections/HeroSection.vue'
import AboutSection from './components/sections/AboutSection.vue'
import WorkSection from './components/sections/WorkSection.vue'
import PortfolioSection from './components/sections/PortfolioSection.vue'
import ContactSection from './components/sections/ContactSection.vue'

onMounted(async () => {
  await nextTick()

  // 우클릭 방지
  document.addEventListener('contextmenu', e => e.preventDefault())

  // 복사 / 잘라내기 방지
  document.addEventListener('copy',  e => e.preventDefault())
  document.addEventListener('cut',   e => e.preventDefault())

  // 드래그 방지
  document.addEventListener('dragstart', e => e.preventDefault())

  // 키보드 단축키 방지 (PrintScreen, Ctrl+C/A/S/P/U, F12)
  document.addEventListener('keydown', e => {
    const ctrl = e.ctrlKey || e.metaKey
    if (
      e.key === 'PrintScreen' ||
      (ctrl && ['c', 'a', 's', 'p', 'u'].includes(e.key.toLowerCase())) ||
      e.key === 'F12'
    ) {
      e.preventDefault()
    }
  })

  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('is-visible')
          observer.unobserve(entry.target)
        }
      })
    },
    { threshold: 0.1, rootMargin: '0px 0px -60px 0px' }
  )

  document.querySelectorAll('.reveal').forEach(el => observer.observe(el))
})
</script>

<template>
  <AppHeader />
  <main>
    <HeroSection />
    <AboutSection />
    <WorkSection />
    <PortfolioSection />
    <ContactSection />
  </main>
  <AppFooter />
</template>
