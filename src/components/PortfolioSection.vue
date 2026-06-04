<template>
  <section class="portfolio" id="portfolio">

    <div class="section-header reveal">
      <div>
        <p class="section-label">Portfolio</p>
        <h2>Moje prace</h2>
      </div>
      <span class="count-pill">{{ filtered.length }} filmów</span>
    </div>

    <div class="tabs reveal reveal-delay-1" role="tablist">
      <button
        v-for="cat in categories"
        :key="cat.id"
        class="tab"
        :class="{ active: activeTab === cat.id }"
        @click="setTab(cat.id)"
        role="tab"
      >
        <span class="tab-emoji">{{ cat.emoji }}</span>
        {{ cat.label }}
        <span class="tab-count">{{ countFor(cat.id) }}</span>
      </button>
    </div>

    <div
      class="video-grid"
      :class="{ 'shorts-grid': activeTab === 'shorts' }"
      :key="gridKey"
    >
      <VideoCard
        v-for="(video, i) in visible"
        :key="video.id"
        :video="video"
        :style="{ animationDelay: `${i * 28}ms` }"
        class="card-animate"
        @open="openModal"
      />
    </div>

    <div v-if="hasMore || expanded" class="show-more-wrap">
      <button class="btn-show-more" :class="{ expanded }" @click="toggle">
        <span>{{ expanded ? 'Zwiń' : `Pokaż wszystkie (${remaining} więcej)` }}</span>
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <polyline points="6 9 12 15 18 9"/>
        </svg>
      </button>
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
import { ref, computed, watch } from 'vue'
import { videos, categories } from '../data/videos.js'
import VideoCard from './VideoCard.vue'
import VideoModal from './VideoModal.vue'

const INITIAL_REGULAR = 12
const INITIAL_SHORTS  = 18

const activeTab     = ref('all')
const expanded      = ref(false)
const gridKey       = ref(0)
const activeId      = ref(null)
const activeIsShort = ref(false)

function byDateDesc(a, b) {
  if (!a.date && !b.date) return 0
  if (!a.date) return 1
  if (!b.date) return -1
  return b.date.localeCompare(a.date)
}

const filtered = computed(() => {
  const list = activeTab.value === 'all'
    ? videos.filter(v => !v.short)
    : videos.filter(v => v.cat === activeTab.value)
  return [...list].sort(byDateDesc)
})

const initialCount = computed(() =>
  activeTab.value === 'shorts' ? INITIAL_SHORTS : INITIAL_REGULAR
)

const visible = computed(() =>
  expanded.value ? filtered.value : filtered.value.slice(0, initialCount.value)
)

const hasMore = computed(() =>
  !expanded.value && filtered.value.length > initialCount.value
)

const remaining = computed(() =>
  filtered.value.length - initialCount.value
)

function countFor(catId) {
  if (catId === 'all') return videos.filter(v => !v.short).length
  return videos.filter(v => v.cat === catId).length
}

function setTab(id) {
  activeTab.value = id
  expanded.value = false
}

function toggle() {
  expanded.value = !expanded.value
}

function openModal(id) {
  const video = videos.find(v => v.id === id)
  activeId.value = id
  activeIsShort.value = !!video?.short
}

watch(activeTab, () => { gridKey.value++ })
</script>

<style scoped>
.portfolio {
  padding: 5rem 3rem;
}

.section-header {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  margin-bottom: 2rem;
  flex-wrap: wrap;
  gap: 1rem;
}

.section-label {
  font-size: 0.6rem;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  color: var(--accent2);
  margin-bottom: 0.5rem;
}

h2 {
  font-family: var(--font-display);
  font-size: clamp(2rem, 4vw, 3.2rem);
  letter-spacing: 0.06em;
  color: var(--text);
  line-height: 1;
}

.count-pill {
  font-size: 0.62rem;
  letter-spacing: 0.1em;
  color: var(--muted);
  background: var(--surface);
  border: 1px solid var(--border);
  padding: 0.3rem 0.9rem;
  align-self: flex-end;
}

/* Tabs */
.tabs {
  display: flex;
  border-bottom: 1px solid var(--border);
  overflow-x: auto;
  scrollbar-width: none;
  margin-bottom: 3px;
}
.tabs::-webkit-scrollbar { display: none; }

.tab {
  background: none;
  border: none;
  border-bottom: 2px solid transparent;
  margin-bottom: -1px;
  padding: 0.75rem 1.2rem;
  font-family: var(--font-body);
  font-size: 0.66rem;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--muted);
  cursor: pointer;
  white-space: nowrap;
  transition: color 0.2s, border-color 0.2s;
  display: flex;
  align-items: center;
  gap: 0.45rem;
}

.tab:hover { color: var(--text); }
.tab.active { color: var(--text); border-bottom-color: var(--accent); }

.tab-emoji {
  font-size: 0.85rem;
  line-height: 1;
  margin-right: 0.1rem;
  filter: saturate(0.7);
  transition: filter 0.2s;
}
.tab:hover .tab-emoji,
.tab.active .tab-emoji { filter: saturate(1); }

.tab-count { font-size: 0.56rem; opacity: 0.45; }
.tab.active .tab-count { color: var(--accent); opacity: 1; }

/* Grids */
.video-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 3px;
}

.shorts-grid {
  grid-template-columns: repeat(9, 1fr);
}

/* Card entrance stagger */
@keyframes cardIn {
  from { opacity: 0; transform: translateY(14px) scale(0.97); }
  to   { opacity: 1; transform: translateY(0) scale(1); }
}

.card-animate {
  animation: cardIn 0.45s cubic-bezier(0.22, 1, 0.36, 1) both;
}

/* Show more */
.show-more-wrap {
  display: flex;
  justify-content: center;
  padding-top: 2rem;
}

.btn-show-more {
  background: none;
  border: 1px solid var(--border2);
  color: var(--muted);
  padding: 0.85rem 2.5rem;
  font-family: var(--font-body);
  font-size: 0.66rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  cursor: pointer;
  transition: color 0.2s, border-color 0.2s, background 0.2s;
  display: flex;
  align-items: center;
  gap: 0.6rem;
}

.btn-show-more:hover {
  color: var(--text);
  border-color: var(--muted);
  background: var(--surface);
}

.btn-show-more svg {
  transition: transform 0.35s cubic-bezier(0.22, 1, 0.36, 1);
}

.btn-show-more.expanded svg {
  transform: rotate(180deg);
}

/* Responsive */
@media (max-width: 1400px) {
  .shorts-grid { grid-template-columns: repeat(8, 1fr); }
}

@media (max-width: 1200px) {
  .video-grid  { grid-template-columns: repeat(3, 1fr); }
  .shorts-grid { grid-template-columns: repeat(7, 1fr); }
}

@media (max-width: 1024px) {
  .portfolio   { padding-left: 2.5rem; padding-right: 2.5rem; }
  .shorts-grid { grid-template-columns: repeat(6, 1fr); }
}

@media (max-width: 700px) {
  .portfolio   { padding-left: 1.5rem; padding-right: 1.5rem; }
  .video-grid  { grid-template-columns: repeat(2, 1fr); }
  .shorts-grid { grid-template-columns: repeat(4, 1fr); }
}

@media (max-width: 480px) {
  .shorts-grid { grid-template-columns: repeat(3, 1fr); }
}
</style>
