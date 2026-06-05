<template>
  <section id="hero" class="hero">
    <div class="hero-bg"></div>
    <div class="hero-content">
      <p class="hero-label">Designer &amp; Publisher</p>

      <!-- 꽃 일러스트 -->
      <div class="hero-flower-wrap" aria-hidden="true">
        <svg class="hero-flower" viewBox="0 0 360 430" fill="none" xmlns="http://www.w3.org/2000/svg">
          <!-- 글로우 -->
          <circle cx="180" cy="185" r="135" fill="rgba(42,122,79,0.06)"/>

          <!-- 뒤쪽 꽃잎 8개 (22.5° 회전, 반투명 — 깊이감) -->
          <g class="petals-back">
            <path d="M180 185 C157 169,151 133,180 86 C209 133,203 169,180 185Z" transform="rotate(22.5 180 185)"  fill="rgba(255,255,255,0.18)"/>
            <path d="M180 185 C157 169,151 133,180 86 C209 133,203 169,180 185Z" transform="rotate(67.5 180 185)"  fill="rgba(255,255,255,0.18)"/>
            <path d="M180 185 C157 169,151 133,180 86 C209 133,203 169,180 185Z" transform="rotate(112.5 180 185)" fill="rgba(255,255,255,0.18)"/>
            <path d="M180 185 C157 169,151 133,180 86 C209 133,203 169,180 185Z" transform="rotate(157.5 180 185)" fill="rgba(255,255,255,0.18)"/>
            <path d="M180 185 C157 169,151 133,180 86 C209 133,203 169,180 185Z" transform="rotate(202.5 180 185)" fill="rgba(255,255,255,0.18)"/>
            <path d="M180 185 C157 169,151 133,180 86 C209 133,203 169,180 185Z" transform="rotate(247.5 180 185)" fill="rgba(255,255,255,0.18)"/>
            <path d="M180 185 C157 169,151 133,180 86 C209 133,203 169,180 185Z" transform="rotate(292.5 180 185)" fill="rgba(255,255,255,0.18)"/>
            <path d="M180 185 C157 169,151 133,180 86 C209 133,203 169,180 185Z" transform="rotate(337.5 180 185)" fill="rgba(255,255,255,0.18)"/>
          </g>

          <!-- 앞쪽 꽃잎 8개 -->
          <g class="petals-front">
            <path d="M180 185 C157 169,151 133,180 86 C209 133,203 169,180 185Z"                              fill="rgba(255,255,255,0.82)" stroke="rgba(255,255,255,0.2)" stroke-width="0.6"/>
            <path d="M180 185 C157 169,151 133,180 86 C209 133,203 169,180 185Z" transform="rotate(45 180 185)"  fill="rgba(255,255,255,0.82)" stroke="rgba(255,255,255,0.2)" stroke-width="0.6"/>
            <path d="M180 185 C157 169,151 133,180 86 C209 133,203 169,180 185Z" transform="rotate(90 180 185)"  fill="rgba(255,255,255,0.82)" stroke="rgba(255,255,255,0.2)" stroke-width="0.6"/>
            <path d="M180 185 C157 169,151 133,180 86 C209 133,203 169,180 185Z" transform="rotate(135 180 185)" fill="rgba(255,255,255,0.82)" stroke="rgba(255,255,255,0.2)" stroke-width="0.6"/>
            <path d="M180 185 C157 169,151 133,180 86 C209 133,203 169,180 185Z" transform="rotate(180 180 185)" fill="rgba(255,255,255,0.82)" stroke="rgba(255,255,255,0.2)" stroke-width="0.6"/>
            <path d="M180 185 C157 169,151 133,180 86 C209 133,203 169,180 185Z" transform="rotate(225 180 185)" fill="rgba(255,255,255,0.82)" stroke="rgba(255,255,255,0.2)" stroke-width="0.6"/>
            <path d="M180 185 C157 169,151 133,180 86 C209 133,203 169,180 185Z" transform="rotate(270 180 185)" fill="rgba(255,255,255,0.82)" stroke="rgba(255,255,255,0.2)" stroke-width="0.6"/>
            <path d="M180 185 C157 169,151 133,180 86 C209 133,203 169,180 185Z" transform="rotate(315 180 185)" fill="rgba(255,255,255,0.82)" stroke="rgba(255,255,255,0.2)" stroke-width="0.6"/>
          </g>

          <!-- 줄기 -->
          <path d="M180 220 C179 262 181 315 180 400" stroke="rgba(255,255,255,0.16)" stroke-width="1.5" stroke-linecap="round"/>

          <!-- 왼쪽 잎 -->
          <path d="M179 305 C156 289,133 268,146 251 C159 234,179 271,179 286Z"
                fill="rgba(42,122,79,0.42)" stroke="rgba(61,153,101,0.4)" stroke-width="1" stroke-linejoin="round"/>

          <!-- 오른쪽 잎 -->
          <path d="M181 345 C204 329,227 308,214 291 C201 274,181 311,181 326Z"
                fill="rgba(42,122,79,0.42)" stroke="rgba(61,153,101,0.4)" stroke-width="1" stroke-linejoin="round"/>

          <!-- 꽃 중앙 (3겹 동심원) -->
          <circle cx="180" cy="185" r="36" fill="#122b1e"/>
          <circle cx="180" cy="185" r="27" fill="#2A7A4F"/>
          <circle cx="180" cy="185" r="16" fill="#3D9965"/>

          <!-- 수술 점 6개 -->
          <circle cx="180" cy="168" r="2"   fill="rgba(255,255,255,0.5)"/>
          <circle cx="195" cy="176" r="2"   fill="rgba(255,255,255,0.5)"/>
          <circle cx="195" cy="194" r="2"   fill="rgba(255,255,255,0.5)"/>
          <circle cx="180" cy="202" r="2"   fill="rgba(255,255,255,0.5)"/>
          <circle cx="165" cy="194" r="2"   fill="rgba(255,255,255,0.5)"/>
          <circle cx="165" cy="176" r="2"   fill="rgba(255,255,255,0.5)"/>
        </svg>
      </div>

      <p class="hero-tagline">
        공간에 생명을 불어넣는<br>
        비주얼 커뮤니케이터
      </p>
      <a href="#about" class="hero-cta">
        <span>더 알아보기</span>
        <svg width="16" height="16" viewBox="0 0 16 16" fill="none" aria-hidden="true">
          <path d="M8 3v10M3 8l5 5 5-5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </a>
    </div>

    <div class="hero-scroll-hint" aria-hidden="true">
      <div class="scroll-line"></div>
      <span>Scroll</span>
    </div>
  </section>
</template>

<script setup>
</script>

<style scoped>
.hero {
  position: relative;
  min-height: 100vh;
  min-height: 100svh;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  background: var(--color-black);
}

.hero-bg {
  position: absolute;
  inset: 0;
  background:
    radial-gradient(ellipse 60% 50% at 70% 40%, rgba(42, 122, 79, 0.10) 0%, transparent 70%),
    radial-gradient(ellipse 40% 60% at 20% 80%, rgba(42, 122, 79, 0.05) 0%, transparent 60%);
}

.hero-content {
  position: relative;
  text-align: center;
  padding: 6rem 1.5rem 4rem;
  animation: fadeUp 1s ease both;
  width: 100%;
  max-width: 600px;
}

.hero-label {
  font-family: var(--font-sans);
  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  color: var(--color-green-light);
  margin-bottom: 2.5rem;
}

/* ── 꽃 일러스트 ── */
.hero-flower-wrap {
  width: 280px;
  max-width: 72vw;
  margin: 0 auto 3rem;
}

.hero-flower {
  width: 100%;
  height: auto;
  display: block;
  animation: flowerBreath 5s ease-in-out infinite;
}

/* 뒤쪽 꽃잎 천천히 회전 */
.petals-back {
  transform-origin: 180px 185px;
  animation: slowSpin 40s linear infinite;
}

@keyframes flowerBreath {
  0%, 100% { transform: scale(1); }
  50%       { transform: scale(1.04); }
}

@keyframes slowSpin {
  from { transform: rotate(0deg); }
  to   { transform: rotate(360deg); }
}

.hero-tagline {
  font-family: var(--font-elegant);
  font-size: clamp(1rem, 2.5vw, 1.4rem);
  font-weight: 300;
  color: rgba(255, 255, 255, 0.55);
  line-height: 1.8;
  letter-spacing: 0.02em;
  margin-bottom: 3rem;
}

.hero-cta {
  display: inline-flex;
  align-items: center;
  gap: 0.6rem;
  font-size: 0.8rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--color-white);
  border: 1px solid rgba(255, 255, 255, 0.2);
  padding: 0.9rem 2rem;
  border-radius: 2px;
  transition: all var(--transition);
  touch-action: manipulation;
}

.hero-cta:hover {
  background: var(--color-green);
  border-color: var(--color-green);
}

/* 스크롤 힌트 */
.hero-scroll-hint {
  position: absolute;
  bottom: 2.5rem;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.75rem;
  color: rgba(255, 255, 255, 0.3);
  font-size: 0.65rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  white-space: nowrap;
}

.scroll-line {
  width: 1px;
  height: 48px;
  background: linear-gradient(to bottom, var(--color-green), transparent);
  animation: scrollDown 2s ease-in-out infinite;
}

@keyframes fadeUp {
  from { opacity: 0; transform: translateY(30px); }
  to   { opacity: 1; transform: translateY(0); }
}

@keyframes scrollDown {
  0%, 100% { opacity: 0.3; transform: scaleY(0.8); }
  50%       { opacity: 1;   transform: scaleY(1); }
}

/* ── 반응형 ── */
@media (max-width: 768px) {
  .hero-content {
    padding: 5rem 1.25rem 5rem;
  }
  .hero-flower-wrap {
    width: 220px;
  }
  .hero-tagline br {
    display: none;
  }
  .hero-scroll-hint {
    display: none;
  }
}

@media (max-width: 480px) {
  .hero-label {
    font-size: 0.65rem;
    letter-spacing: 0.2em;
  }
  .hero-flower-wrap {
    width: 180px;
  }
  .hero-cta {
    padding: 0.8rem 1.5rem;
    font-size: 0.75rem;
  }
}
</style>
