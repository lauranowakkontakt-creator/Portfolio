<template>
  <button class="video-card" :class="{ short: video.short }" @click="$emit('open', video.id)" type="button">
    <div class="v-fallback">
      <svg viewBox="0 0 24 24" width="20" height="20" fill="var(--accent)">
        <path d="M8 5v14l11-7z" />
      </svg>
    </div>

    <img
      v-show="!imgError"
      class="v-thumb"
      :class="{ loaded: imgLoaded }"
      :src="thumbUrl"
      :alt="`${video.title || 'Film'} — Laura Nowak`"
      @load="imgLoaded = true"
      @error="imgError = true"
    />

    <div class="v-bar" v-if="video.title || video.type">
      <p class="v-type" v-if="video.type">{{ video.type }}</p>
      <p class="v-title" v-if="video.title">{{ video.title }}</p>
    </div>

    <div class="v-play">
      <svg viewBox="0 0 24 24" width="18" height="18" fill="white">
        <path d="M8 5v14l11-7z" />
      </svg>
    </div>

    <div class="v-accent-line"></div>
  </button>
</template>

<script setup>
import { ref, computed } from 'vue'

const props = defineProps({
  video: { type: Object, required: true },
})

defineEmits(['open'])

const imgLoaded = ref(false)
const imgError  = ref(false)

const thumbUrl = computed(
  () => `https://i.ytimg.com/vi/${props.video.id}/hqdefault.jpg`
)
</script>

<style scoped>
.video-card {
  position: relative;
  overflow: hidden;
  background: var(--surface);
  border: none;
  display: block;
  width: 100%;
  aspect-ratio: 16 / 9;
  cursor: pointer;
  padding: 0;
}

.video-card.short {
  aspect-ratio: 9 / 16;
}

.v-accent-line {
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 2px;
  background: var(--accent);
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.35s ease;
  z-index: 3;
}

.video-card:hover .v-accent-line {
  transform: scaleX(1);
}

.v-fallback {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--surface);
  opacity: 0.5;
}

.v-thumb {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  opacity: 0;
  transition: opacity 0.4s, transform 0.55s ease;
}

.v-thumb.loaded {
  opacity: 1;
}

.video-card:hover .v-thumb {
  transform: scale(1.04);
}

.v-bar {
  position: absolute;
  bottom: 0; left: 0; right: 0;
  background: linear-gradient(to top, rgba(0,0,0,0.85) 0%, transparent 100%);
  padding: 1rem 0.85rem 0.7rem;
  z-index: 2;
}

.v-type {
  font-size: 0.55rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--accent);
  margin-bottom: 0.15rem;
}

.v-title {
  font-size: 0.78rem;
  color: #f0ede8;
  line-height: 1.3;
}

.v-play {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2;
  opacity: 0;
  transition: opacity 0.25s;
}

.v-play::before {
  content: '';
  width: 44px;
  height: 44px;
  border-radius: 50%;
  background: rgba(217, 82, 45, 0.88);
  position: absolute;
}

.v-play svg {
  position: relative;
  z-index: 1;
  margin-left: 2px;
}

.video-card:hover .v-play {
  opacity: 1;
}
</style>
