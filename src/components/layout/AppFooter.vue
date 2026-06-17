<template>
  <footer class="footer">
    <div class="container footer-inner">
      <img src="../../assets/luma_logo_png.png" alt="Luma" class="footer-logo" />
      <p class="footer-copy">© {{ year }} LUMA. All rights reserved.</p>
    </div>
  </footer>

  <Teleport to="body">
    <button
      class="back-top"
      :class="{ visible: isVisible }"
      @click="scrollToTop"
      aria-label="맨 위로 이동"
    >
      <svg width="18" height="18" viewBox="0 0 18 18" fill="none">
        <path d="M9 14V4M4 9l5-5 5 5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </button>
  </Teleport>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const year = new Date().getFullYear()
const isVisible = ref(false)

function onScroll() {
  isVisible.value = window.scrollY > 300
}

function scrollToTop() {
  window.scrollTo({ top: 0, behavior: 'smooth' })
}

onMounted(() => window.addEventListener('scroll', onScroll, { passive: true }))
onUnmounted(() => window.removeEventListener('scroll', onScroll))
</script>

<style scoped>
@import '../../style/footer.css';
</style>
