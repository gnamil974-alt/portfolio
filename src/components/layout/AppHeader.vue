<template>
  <header class="header" :class="{ scrolled: isScrolled, 'is-dark': isDarkSection }">
    <div class="header-inner">
      <a href="#hero" class="logo">
        <img src="../../assets/luma_logo_png.png" alt="Luma" class="logo-img" />
      </a>

      <nav class="nav">
        <a
          v-for="item in navItems"
          :key="item.href"
          :href="item.href"
          class="nav-link"
        >{{ item.label }}</a>
      </nav>

      <button class="menu-btn" :class="{ open: menuOpen }" @click="toggleMenu" aria-label="메뉴">
        <span></span>
        <span></span>
      </button>
    </div>
  </header>

  <Teleport to="body">
    <div class="mobile-menu" :class="{ open: menuOpen }">
      <button class="mobile-menu-close" @click="menuOpen = false" aria-label="닫기">
        <span></span>
        <span></span>
      </button>
      <a
        v-for="item in navItems"
        :key="item.href"
        :href="item.href"
        class="mobile-nav-link"
        @click="menuOpen = false"
      >{{ item.label }}</a>
    </div>
  </Teleport>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const isDarkSection = ref(false)
const menuOpen = ref(false)

const navItems = [
  { href: '#about',     label: 'About' },
  { href: '#work',      label: 'Work' },
  { href: '#portfolio', label: 'Portfolio' },
  { href: '#contact',   label: 'Contact' },
]

function updateSectionTheme() {
  const sections = document.querySelectorAll('section[data-theme]')
  const checkY = 80
  let theme = 'light'
  sections.forEach(section => {
    const rect = section.getBoundingClientRect()
    if (rect.top <= checkY && rect.bottom > checkY) {
      theme = section.dataset.theme || 'light'
    }
  })
  isDarkSection.value = theme === 'dark'
}

function onScroll() {
  isScrolled.value = window.scrollY > 60
  updateSectionTheme()
}

function toggleMenu() {
  menuOpen.value = !menuOpen.value
}

onMounted(() => {
  window.addEventListener('scroll', onScroll, { passive: true })
  updateSectionTheme()
})
onUnmounted(() => window.removeEventListener('scroll', onScroll))
</script>

<style scoped>
@import '../../style/header.css';
</style>
