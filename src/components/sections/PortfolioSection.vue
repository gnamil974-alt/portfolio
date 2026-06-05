<template>
  <section id="portfolio" class="section portfolio">
    <div class="container">
      <div class="portfolio-header">
        <div>
          <span class="section-label">Portfolio</span>
          <h2 class="section-title">작업 결과물</h2>
        </div>
        <div class="filter-tabs">
          <button
            v-for="cat in categories"
            :key="cat"
            class="filter-btn"
            :class="{ active: activeCategory === cat }"
            @click="activeCategory = cat"
          >{{ cat }}</button>
        </div>
      </div>

      <div class="portfolio-grid">
        <div
          v-for="item in filteredItems"
          :key="item.id"
          class="portfolio-item"
          :class="`col-${item.span}`"
        >
          <div class="portfolio-thumb">
            <div class="thumb-placeholder" :style="{ background: item.bg }">
              <span>{{ item.title }}</span>
            </div>
            <div class="portfolio-overlay">
              <div class="overlay-content">
                <p class="overlay-category">{{ item.category }}</p>
                <h3 class="overlay-title">{{ item.title }}</h3>
                <p class="overlay-year">{{ item.year }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'

const categories = ['All', 'Brand', 'Editorial', 'Web', 'Package']
const activeCategory = ref('All')

const items = [
  { id: 1, title: 'Bloom Bakery',      category: 'Brand',     year: '2024', span: 2, bg: '#E8EDE9' },
  { id: 2, title: 'MODO Annual Report', category: 'Editorial', year: '2024', span: 1, bg: '#EDE8E3' },
  { id: 3, title: 'Greens Market',     category: 'Package',   year: '2023', span: 1, bg: '#E3EDE8' },
  { id: 4, title: 'Noir Studio',       category: 'Web',       year: '2023', span: 1, bg: '#E8E8ED' },
  { id: 5, title: 'Lune Perfume',      category: 'Brand',     year: '2023', span: 2, bg: '#EDE3E8' },
  { id: 6, title: 'Arche Magazine',    category: 'Editorial', year: '2022', span: 1, bg: '#EDE8E3' },
]

const filteredItems = computed(() =>
  activeCategory.value === 'All'
    ? items
    : items.filter(i => i.category === activeCategory.value)
)
</script>

<style scoped>
.portfolio {
  background: var(--color-off-white);
}

.portfolio-header {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  margin-bottom: 3.5rem;
  gap: 1.5rem;
  flex-wrap: wrap;
}

/* 필터 */
.filter-tabs {
  display: flex;
  flex-wrap: wrap;
  gap: 0.25rem;
}

.filter-btn {
  font-size: 0.75rem;
  font-weight: 500;
  letter-spacing: 0.08em;
  color: var(--color-gray);
  padding: 0.4rem 0.9rem;
  border: 1px solid transparent;
  border-radius: 2px;
  transition: all var(--transition);
  touch-action: manipulation;
}

.filter-btn:hover {
  color: var(--color-black);
}

.filter-btn.active {
  color: var(--color-green);
  border-color: var(--color-green);
  background: var(--color-green-muted);
}

/* 그리드 */
.portfolio-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.25rem;
}

.portfolio-item {
  overflow: hidden;
}

.portfolio-item.col-2 {
  grid-column: span 2;
}

.portfolio-item.col-1 {
  grid-column: span 1;
}

.portfolio-thumb {
  position: relative;
  aspect-ratio: 4/3;
  overflow: hidden;
  cursor: pointer;
}

.portfolio-item.col-2 .portfolio-thumb {
  aspect-ratio: 16/9;
}

.thumb-placeholder {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: var(--font-serif);
  font-size: 1rem;
  color: rgba(0, 0, 0, 0.3);
  transition: transform var(--transition);
}

.portfolio-thumb:hover .thumb-placeholder {
  transform: scale(1.04);
}

/* 오버레이 */
.portfolio-overlay {
  position: absolute;
  inset: 0;
  background: rgba(10, 10, 10, 0);
  display: flex;
  align-items: flex-end;
  padding: 1.25rem;
  transition: background var(--transition);
}

.portfolio-thumb:hover .portfolio-overlay {
  background: rgba(10, 10, 10, 0.75);
}

.overlay-content {
  transform: translateY(8px);
  opacity: 0;
  transition: all var(--transition);
}

.portfolio-thumb:hover .overlay-content {
  transform: translateY(0);
  opacity: 1;
}

.overlay-category {
  font-size: 0.65rem;
  font-weight: 500;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--color-green-light);
  margin-bottom: 0.35rem;
}

.overlay-title {
  font-family: var(--font-serif);
  font-size: 1.1rem;
  font-weight: 500;
  color: var(--color-white);
  margin-bottom: 0.2rem;
}

.overlay-year {
  font-size: 0.75rem;
  color: rgba(255, 255, 255, 0.5);
}

/* ── 반응형 ── */
@media (max-width: 1024px) {
  .portfolio-grid {
    gap: 1rem;
  }
}

@media (max-width: 768px) {
  .portfolio-header {
    flex-direction: column;
    align-items: flex-start;
    margin-bottom: 2.5rem;
  }
  .filter-tabs {
    width: 100%;
  }
  .filter-btn {
    flex: 1 0 auto;
    text-align: center;
  }
  .portfolio-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 0.75rem;
  }
  .portfolio-item.col-2 {
    grid-column: span 2;
  }
  /* 모바일에서는 오버레이 항상 보이게 */
  .portfolio-overlay {
    background: rgba(10, 10, 10, 0.5);
  }
  .overlay-content {
    opacity: 1;
    transform: none;
  }
}

@media (max-width: 480px) {
  .portfolio-grid {
    grid-template-columns: 1fr;
    gap: 0.75rem;
  }
  .portfolio-item.col-2 {
    grid-column: span 1;
  }
  .portfolio-item.col-2 .portfolio-thumb {
    aspect-ratio: 4/3;
  }
}
</style>
