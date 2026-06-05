<template>
  <header class="header" :class="{ scrolled: isScrolled, 'on-dark': !isScrolled }">
    <div class="header-inner">
      <a href="#hero" class="logo">
        <!-- 세이지 잎 마크 -->
        <svg class="logo-mark" viewBox="0 0 22 30" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <!-- 줄기 -->
          <path d="M11 29 C11 22 11 14 11 4" stroke="currentColor" stroke-width="1.2" stroke-linecap="round" opacity="0.6"/>
          <!-- 위 잎 -->
          <path d="M11 4 C5 4 1 9 2 14 C3 18 7 20 11 18 C15 20 19 18 20 14 C21 9 17 4 11 4Z" fill="currentColor"/>
          <!-- 왼쪽 작은 잎 -->
          <path d="M11 16 C8 14 4 14 3 17 C2 20 5 22 8 21 C9 21 11 19 11 17Z" fill="currentColor" opacity="0.55"/>
          <!-- 오른쪽 작은 잎 -->
          <path d="M11 20 C14 18 18 18 19 21 C20 24 17 26 14 25 C13 25 11 23 11 21Z" fill="currentColor" opacity="0.55"/>
        </svg>
        <span class="logo-name">Sage</span>
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
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const menuOpen = ref(false)

const navItems = [
  { href: '#about', label: 'About' },
  { href: '#work', label: 'Work' },
  { href: '#portfolio', label: 'Portfolio' },
  { href: '#contact', label: 'Contact' },
]

function onScroll() {
  isScrolled.value = window.scrollY > 60
}

function toggleMenu() {
  menuOpen.value = !menuOpen.value
}

onMounted(() => window.addEventListener('scroll', onScroll, { passive: true }))
onUnmounted(() => window.removeEventListener('scroll', onScroll))
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  padding: 1.5rem 2rem;
  transition: background var(--transition), padding var(--transition), box-shadow var(--transition);
}

/* 히어로 위에 있을 때 — 다크 배경이므로 텍스트 흰색 */
.header.on-dark .logo {
  color: var(--color-white);
}
.header.on-dark .logo-mark {
  color: var(--color-green-light);
}
.header.on-dark .nav-link {
  color: rgba(255, 255, 255, 0.6);
}
.header.on-dark .nav-link:hover {
  color: var(--color-white);
}
.header.on-dark .menu-btn span {
  background: var(--color-white);
}

/* 스크롤 후 — 화이트 배경 */
.header.scrolled {
  background: rgba(255, 255, 255, 0.96);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  padding: 1rem 2rem;
  box-shadow: 0 1px 0 var(--color-gray-light);
}

.header-inner {
  max-width: var(--max-width);
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

/* 로고 */
.logo {
  display: flex;
  align-items: center;
  gap: 0.55rem;
  color: var(--color-black);
  transition: color var(--transition), opacity var(--transition);
}

.logo:hover {
  opacity: 0.75;
}

.logo-mark {
  width: 16px;
  height: 22px;
  color: var(--color-green);
  flex-shrink: 0;
  transition: color var(--transition);
}

.logo-name {
  font-family: var(--font-serif);
  font-size: 1.55rem;
  font-weight: 500;
  font-style: italic;
  letter-spacing: 0.01em;
  line-height: 1;
}

/* 데스크탑 네비 */
.nav {
  display: flex;
  gap: 2.5rem;
}

.nav-link {
  font-size: 0.8rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--color-gray);
  position: relative;
  transition: color var(--transition);
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: -3px;
  left: 0;
  width: 0;
  height: 1px;
  background: var(--color-green);
  transition: width var(--transition);
}

.nav-link:hover {
  color: var(--color-black);
}

.nav-link:hover::after {
  width: 100%;
}

/* 햄버거 버튼 */
.menu-btn {
  display: none;
  flex-direction: column;
  gap: 6px;
  width: 28px;
  padding: 4px 0;
  cursor: pointer;
}

.menu-btn span {
  display: block;
  height: 1.5px;
  background: var(--color-black);
  transition: transform var(--transition), opacity var(--transition), background var(--transition);
  transform-origin: center;
}

.menu-btn.open span:first-child {
  transform: translateY(3.75px) rotate(45deg);
}
.menu-btn.open span:last-child {
  transform: translateY(-3.75px) rotate(-45deg);
}

/* 모바일 전체화면 메뉴 */
.mobile-menu {
  display: none;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 2.5rem;
  background: var(--color-black);
  position: fixed;
  inset: 0;
  z-index: 99;
  transform: translateX(100%);
  transition: transform 0.5s cubic-bezier(0.76, 0, 0.24, 1);
}

.mobile-menu.open {
  transform: translateX(0);
}

.mobile-menu-close {
  position: absolute;
  top: 1.5rem;
  right: 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 0;
  width: 28px;
  height: 28px;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}

.mobile-menu-close span {
  display: block;
  width: 20px;
  height: 1.5px;
  background: rgba(255, 255, 255, 0.6);
  position: absolute;
}
.mobile-menu-close span:first-child { transform: rotate(45deg); }
.mobile-menu-close span:last-child  { transform: rotate(-45deg); }

.mobile-nav-link {
  font-family: var(--font-serif);
  font-size: clamp(2rem, 8vw, 3rem);
  color: rgba(255, 255, 255, 0.7);
  transition: color var(--transition);
  letter-spacing: 0.02em;
}

.mobile-nav-link:hover {
  color: var(--color-green-light);
}

/* ── 반응형 ── */
@media (max-width: 768px) {
  .header {
    padding: 1.25rem 1.25rem;
  }
  .header.scrolled {
    padding: 1rem 1.25rem;
  }
  .nav {
    display: none;
  }
  .menu-btn {
    display: flex;
  }
  .mobile-menu {
    display: flex;
  }
}
</style>
