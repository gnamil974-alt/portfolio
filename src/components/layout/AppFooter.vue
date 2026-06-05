<template>
  <footer class="footer">
    <div class="container footer-inner">
      <p class="footer-name">Sage.</p>
      <p class="footer-copy">© {{ year }} Sage. All rights reserved.</p>
    </div>
  </footer>
</template>

<script setup>
const year = new Date().getFullYear()
</script>

<style scoped>
.footer {
  background: var(--color-black);
  border-top: 1px solid rgba(255, 255, 255, 0.06);
  padding: 2rem 0;
}

.footer-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.footer-name {
  font-family: var(--font-serif);
  font-size: 1.1rem;
  color: rgba(255, 255, 255, 0.5);
  font-style: italic;
}

.footer-copy {
  font-size: 0.75rem;
  color: rgba(255, 255, 255, 0.25);
  letter-spacing: 0.05em;
}

@media (max-width: 580px) {
  .footer-inner {
    flex-direction: column;
    gap: 0.75rem;
    text-align: center;
  }
}
</style>
