<template>
  <section class="portfolio" id="portfolio">
    <div class="section-header">
      <div class="section-label">Portfolio</div>
      <h2>Moje prace</h2>
      <p class="video-count">{{ filtered.length }} filmów</p>
    </div>

    <!-- Zakładki kategorii -->
    <div class="tabs" role="tablist">
      <button
        v-for="cat in categories"
        :key="cat.id"
        class="tab"
        :class="{ active: activeTab === cat.id }"
        @click="activeTab = cat.id"
        role="tab"
      >
        {{ cat.label }}
        <span class="tab-count">{{ countFor(cat.id) }}</span>
      </button>
    </div>

    <!-- Siatka filmów -->
    <div class="video-grid" :class="{ 'shorts-grid': activeTab === 'shorts' }">
      <VideoCard
        v-for="video in filtered"
        :key="video.id"
        :video="video"
        @open="openModal"
      />
    </div>

    <VideoModal
      v-if="activeId"
      :videoId="activeId"
      :isShort="activeIsShort"
      @close="activeId = null"
    />
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'
import { videos, categories } from '../data/videos.js'
import VideoCard from './VideoCard.vue'
import VideoModal from './VideoModal.vue'

const activeTab = ref('all')
const activeId   = ref(null)
const activeIsShort = ref(false)

function byDateDesc(a, b) {
  if (!a.date && !b.date) return 0
  if (!a.date) return 1
  if (!b.date) return -1
  return b.date.localeCompare(a.date)
}

const filtered = computed(() => {
  const list = activeTab.value === 'all'
    ? videos
    : videos.filter(v => v.cat === activeTab.value)
  return [...list].sort(byDateDesc)
})

function countFor(catId) {
  if (catId === 'all') return videos.length
  return videos.filter(v => v.cat === catId).length
}

function openModal(id) {
  const video = videos.find(v => v.id === id)
  activeId.value = id
  activeIsShort.value = !!video?.short
}
</script>

<style scoped>
.portfolio {
  padding: 5rem 4rem;
}

.section-header {
  margin-bottom: 2rem;
  display: flex;
  align-items: baseline;
  gap: 1.5rem;
  flex-wrap: wrap;
}

.section-label {
  font-size: 0.68rem;
  letter-spacing: 0.28em;
  text-transform: uppercase;
  color: var(--accent);
}

h2 {
  font-family: var(--font-display);
  font-weight: 700;
  font-size: clamp(1.8rem, 3.5vw, 2.8rem);
  color: var(--text);
  letter-spacing: -0.02em;
}

.video-count {
  font-size: 0.72rem;
  color: var(--muted);
  letter-spacing: 0.08em;
  margin-left: auto;
}

/* Zakładki */
.tabs {
  display: flex;
  gap: 0;
  margin-bottom: 3px;
  border-bottom: 1px solid var(--border);
  overflow-x: auto;
  scrollbar-width: none;
}

.tabs::-webkit-scrollbar { display: none; }

.tab {
  background: none;
  border: none;
  border-bottom: 2px solid transparent;
  margin-bottom: -1px;
  padding: 0.75rem 1.2rem;
  font-family: var(--font-body);
  font-size: 0.72rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--muted);
  cursor: pointer;
  white-space: nowrap;
  transition: color 0.2s, border-color 0.2s;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.tab:hover {
  color: var(--text);
}

.tab.active {
  color: var(--text);
  border-bottom-color: var(--accent);
}

.tab-count {
  font-size: 0.62rem;
  color: var(--muted);
  opacity: 0.6;
}

.tab.active .tab-count {
  color: var(--accent);
  opacity: 1;
}

/* Siatka standardowa */
.video-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 3px;
}

/* Siatka dla shorts (pionowe) */
.shorts-grid {
  grid-template-columns: repeat(6, 1fr);
}

@media (max-width: 1200px) {
  .video-grid { grid-template-columns: repeat(3, 1fr); }
  .shorts-grid { grid-template-columns: repeat(5, 1fr); }
}

@media (max-width: 1024px) {
  .portfolio { padding-left: 2.5rem; padding-right: 2.5rem; }
  .video-grid { grid-template-columns: repeat(3, 1fr); }
  .shorts-grid { grid-template-columns: repeat(4, 1fr); }
}

@media (max-width: 700px) {
  .portfolio { padding-left: 1.5rem; padding-right: 1.5rem; }
  .video-grid { grid-template-columns: repeat(2, 1fr); }
  .shorts-grid { grid-template-columns: repeat(3, 1fr); }
  .video-count { margin-left: 0; }
}
</style>
