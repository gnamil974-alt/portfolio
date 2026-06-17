<template>
  <section id="contact" class="section contact" data-theme="dark">
    <div class="container">

      <!-- 헤더 -->
      <div class="contact-header reveal">
        <span class="contact-badge">Contact</span>
        <h2 class="contact-title reveal delay-1">Get in Touch.</h2>
        <p class="contact-desc reveal delay-2">
          Great design starts with a great conversation.<br>
          Let's talk about what you need.
        </p>
      </div>

      <!-- 이메일 + 소셜 -->
      <div class="contact-body reveal delay-3">
        <a :href="`mailto:${email}`" class="email-link">
          <div class="email-block">
            <span class="email-label">Email</span>
            <span class="email-address">{{ email }}</span>
          </div>
          <div class="email-arrow" aria-hidden="true">
            <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
              <path d="M4 10h12M11 5l5 5-5 5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </div>
        </a>

        <div class="social-links">
          <a
            v-for="s in socials"
            :key="s.label"
            :href="s.href"
            target="_blank"
            rel="noopener noreferrer"
            class="social-link"
          >{{ s.label }}</a>
        </div>
      </div>

    </div>
  </section>
</template>

<script setup>
const email = 'gnamil974@gmail.com'
const socials = [
  { label: 'Instagram', href: 'https://instagram.com' },
  { label: 'Behance',   href: 'https://behance.net' },
  { label: 'LinkedIn',  href: 'https://linkedin.com' },
]
</script>

<style scoped>
@import '../../style/contact.css';
</style>
