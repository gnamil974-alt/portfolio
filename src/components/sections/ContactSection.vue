<template>
  <section id="contact" class="section contact">
    <div class="container">
      <div class="contact-inner">
        <div class="contact-left">
          <span class="section-label">Contact</span>
          <h2 class="section-title">함께 만들어가요</h2>
          <p class="contact-desc">
            새로운 프로젝트, 협업 제안, 또는 단순한 인사도 환영합니다.
            언제든지 편하게 연락해 주세요.
          </p>
        </div>

        <div class="contact-right">
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

          <div class="contact-divider"></div>

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
    </div>
  </section>
</template>

<script setup>
const email = 'hello@kimmirae.com'
const socials = [
  { label: 'Instagram', href: 'https://instagram.com' },
  { label: 'Behance', href: 'https://behance.net' },
  { label: 'LinkedIn', href: 'https://linkedin.com' },
]
</script>

<style scoped>
.contact {
  background: var(--color-black);
}

.contact-inner {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 6rem;
  align-items: center;
}

.section-label {
  color: var(--color-green-light);
}

.section-title {
  color: var(--color-white);
  margin-bottom: 1.5rem;
}

.contact-desc {
  font-size: 1rem;
  color: rgba(255, 255, 255, 0.45);
  line-height: 1.9;
}

/* 이메일 */
.email-link {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
  padding: 1.75rem 1.75rem;
  border: 1px solid rgba(255, 255, 255, 0.12);
  transition: all var(--transition);
  margin-bottom: 2rem;
  touch-action: manipulation;
}

.email-link:hover {
  border-color: var(--color-green);
  background: rgba(42, 122, 79, 0.08);
}

.email-block {
  min-width: 0;
}

.email-label {
  display: block;
  font-size: 0.65rem;
  font-weight: 500;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--color-green-light);
  margin-bottom: 0.5rem;
}

.email-address {
  font-family: var(--font-elegant);
  font-size: clamp(1rem, 3vw, 1.3rem);
  color: var(--color-white);
  letter-spacing: 0.02em;
  word-break: break-all;
}

.email-arrow {
  color: rgba(255, 255, 255, 0.3);
  transition: color var(--transition), transform var(--transition);
  flex-shrink: 0;
}

.email-link:hover .email-arrow {
  color: var(--color-green-light);
  transform: translateX(4px);
}

/* 구분선 */
.contact-divider {
  height: 1px;
  background: rgba(255, 255, 255, 0.08);
  margin-bottom: 2rem;
}

/* 소셜 */
.social-links {
  display: flex;
  flex-wrap: wrap;
  gap: 1.5rem 2rem;
}

.social-link {
  font-size: 0.8rem;
  font-weight: 500;
  letter-spacing: 0.08em;
  color: rgba(255, 255, 255, 0.35);
  transition: color var(--transition);
  position: relative;
}

.social-link::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 0;
  height: 1px;
  background: var(--color-green-light);
  transition: width var(--transition);
}

.social-link:hover {
  color: var(--color-white);
}

.social-link:hover::after {
  width: 100%;
}

/* ── 반응형 ── */
@media (max-width: 1024px) {
  .contact-inner {
    gap: 4rem;
  }
}

@media (max-width: 768px) {
  .contact-inner {
    grid-template-columns: 1fr;
    gap: 3rem;
  }
  .contact-desc br {
    display: none;
  }
  .email-link {
    padding: 1.25rem;
  }
}

@media (max-width: 480px) {
  .email-address {
    font-size: 0.95rem;
  }
  .social-links {
    gap: 1.25rem;
  }
}
</style>
