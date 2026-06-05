<template>
  <section id="about" class="section about">
    <div class="container">
      <div class="about-grid">
        <!-- 왼쪽: 프로필 이미지 영역 -->
        <div class="about-visual">
          <div class="profile-frame">
            <div class="profile-placeholder">
              <span>Photo</span>
            </div>
            <div class="frame-accent"></div>
          </div>
        </div>

        <!-- 오른쪽: 텍스트 -->
        <div class="about-text">
          <span class="section-label">About</span>
          <h2 class="section-title">안녕하세요,<br>디자이너 김미래입니다.</h2>

          <p class="about-desc">
            10년 이상의 경력을 바탕으로 브랜드 아이덴티티, 편집 디자인, 웹 퍼블리싱을 아우르는
            크리에이티브 디자이너입니다. 시각적 언어로 브랜드의 이야기를 전달하고,
            사용자와 콘텐츠 사이의 완벽한 접점을 만들어냅니다.
          </p>

          <div class="skills">
            <div class="skill-group">
              <p class="skill-category">Design</p>
              <ul>
                <li v-for="s in skills.design" :key="s">{{ s }}</li>
              </ul>
            </div>
            <div class="skill-group">
              <p class="skill-category">Publishing</p>
              <ul>
                <li v-for="s in skills.publishing" :key="s">{{ s }}</li>
              </ul>
            </div>
            <div class="skill-group">
              <p class="skill-category">Tools</p>
              <ul>
                <li v-for="s in skills.tools" :key="s">{{ s }}</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const skills = {
  design: ['Brand Identity', 'Editorial Design', 'UI/UX Design', 'Typography'],
  publishing: ['Web Publishing', 'HTML/CSS', 'Responsive Design', 'Cross-browser'],
  tools: ['Figma', 'Illustrator', 'Photoshop', 'InDesign'],
}
</script>

<style scoped>
.about {
  background: var(--color-off-white);
}

.about-grid {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  gap: 6rem;
  align-items: center;
}

/* 프로필 이미지 */
.about-visual {
  position: relative;
}

.profile-frame {
  position: relative;
  aspect-ratio: 3/4;
  max-width: 360px;
  overflow: visible;
}

.profile-placeholder {
  width: 100%;
  height: 100%;
  background: var(--color-gray-light);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.8rem;
  letter-spacing: 0.1em;
  color: var(--color-gray);
  text-transform: uppercase;
}

.frame-accent {
  position: absolute;
  bottom: -1.5rem;
  right: -1.5rem;
  width: 60%;
  height: 60%;
  border: 2px solid var(--color-green);
  pointer-events: none;
}

/* 텍스트 */
.about-text {
  padding: 2rem 0;
}

.section-title {
  margin-bottom: 1.5rem;
}

.about-desc {
  font-size: 1rem;
  color: var(--color-gray);
  line-height: 1.9;
  margin-bottom: 3rem;
}

/* 스킬 */
.skills {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
}

.skill-category {
  font-size: 0.7rem;
  font-weight: 600;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--color-green);
  margin-bottom: 0.75rem;
}

.skill-group ul {
  display: flex;
  flex-direction: column;
  gap: 0.35rem;
}

.skill-group li {
  font-size: 0.875rem;
  color: var(--color-dark);
  position: relative;
  padding-left: 0.75rem;
}

.skill-group li::before {
  content: '';
  position: absolute;
  left: 0;
  top: 50%;
  transform: translateY(-50%);
  width: 3px;
  height: 3px;
  background: var(--color-green);
  border-radius: 50%;
}

/* ── 반응형 ── */
@media (max-width: 1024px) {
  .about-grid {
    gap: 4rem;
  }
}

@media (max-width: 768px) {
  .about-grid {
    grid-template-columns: 1fr;
    gap: 3rem;
  }
  .about-visual {
    display: flex;
    justify-content: center;
  }
  .profile-frame {
    max-width: 240px;
    aspect-ratio: 1/1;
  }
  .frame-accent {
    bottom: -1rem;
    right: -1rem;
  }
  .about-text {
    padding: 0;
  }
  .skills {
    grid-template-columns: repeat(3, 1fr);
    gap: 1.25rem;
  }
}

@media (max-width: 480px) {
  .skills {
    grid-template-columns: 1fr 1fr;
    gap: 1.5rem;
  }
  .skill-group:last-child {
    grid-column: span 2;
  }
}
</style>
