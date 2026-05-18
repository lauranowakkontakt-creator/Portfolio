<template>
  <button
    class="video-card"
    :class="{ short: video.short, loaded: imgLoaded }"
    @click="$emit('open', video.id)"
    type="button"
  >
    <!-- Skeleton shimmer -->
    <div class="v-skeleton"></div>

    <img
      v-show="!imgError"
      class="v-thumb"
      :class="{ visible: imgLoaded }"
      :src="thumbUrl"
      :alt="`${video.title || 'Film'} — Laura Nowak`"
      @load="imgLoaded = true"
      @error="onError"
    />

    <!-- dark overlay on hover -->
    <div class="v-overlay"></div>

    <!-- bottom info bar -->
    <div class="v-bar">
      <p class="v-title" v-if="video.title">{{ video.title }}</p>
    </div>

    <!-- play button -->
    <div class="v-play">
      <div class="v-play-ring"></div>
      <svg viewBox="0 0 24 24" :width="video.short ? 14 : 18" :height="video.short ? 14 : 18" fill="white">
        <path d="M8 5v14l11-7z" />
      </svg>
    </div>

    <!-- top accent line -->
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

function onError() {
  imgError.value = true
}
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

/* Skeleton shimmer */
.v-skeleton {
  position: absolute;
  inset: 0;
  background: linear-gradient(90deg,
    var(--surface) 0%,
    #1e1e1e 50%,
    var(--surface) 100%
  );
  background-size: 200% 100%;
  animation: shimmer 1.8s ease-in-out infinite;
  z-index: 0;
  transition: opacity 0.4s;
}

.video-card.loaded .v-skeleton {
  opacity: 0;
  pointer-events: none;
}

@keyframes shimmer {
  0%   { background-position: 200% 0; }
  100% { background-position: -200% 0; }
}

/* Thumbnail */
.v-thumb {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  opacity: 0;
  transition: opacity 0.45s ease, transform 0.6s cubic-bezier(0.22, 1, 0.36, 1);
  z-index: 1;
}

.v-thumb.visible { opacity: 1; }

.video-card:hover .v-thumb { transform: scale(1.07); filter: contrast(1.08) saturate(1.1); }

/* Dark overlay */
.v-overlay {
  position: absolute;
  inset: 0;
  background: rgba(0, 0, 0, 0);
  transition: background 0.25s;
  z-index: 2;
}

.video-card:hover .v-overlay {
  background: rgba(0, 0, 0, 0.42);
}

/* Bottom info bar */
.v-bar {
  position: absolute;
  bottom: 0; left: 0; right: 0;
  background: linear-gradient(to top, rgba(8,8,8,0.96) 0%, rgba(8,8,8,0.4) 70%, transparent 100%);
  padding: 2rem 1rem 0.85rem;
  z-index: 3;
  opacity: 0.85;
  transition: opacity 0.3s, transform 0.4s cubic-bezier(0.22, 1, 0.36, 1);
}

.video-card:hover .v-bar {
  opacity: 1;
}

.v-type {
  font-family: var(--font-display);
  font-size: 0.62rem;
  letter-spacing: 0.32em;
  text-transform: uppercase;
  color: var(--accent2);
  margin-bottom: 0.35rem;
  display: inline-flex;
  align-items: center;
  gap: 6px;
}

.v-type::before {
  content: '';
  width: 14px;
  height: 1px;
  background: var(--accent2);
  opacity: 0.7;
}

.v-title {
  font-family: var(--font-display);
  font-size: 0.95rem;
  color: #f0ede8;
  line-height: 1.15;
  letter-spacing: 0.06em;
  text-transform: uppercase;
}

/* Play button */
.v-play {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 4;
  opacity: 0;
  transform: scale(0.75);
  transition: opacity 0.2s, transform 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
}

.video-card:hover .v-play {
  opacity: 1;
  transform: scale(1);
}

.v-play-ring {
  position: absolute;
  width: 46px;
  height: 46px;
  border-radius: 50%;
  background: var(--accent);
  box-shadow: 0 0 24px rgba(201, 75, 40, 0.6);
  transition: box-shadow 0.2s;
}

.video-card.short .v-play-ring {
  width: 32px;
  height: 32px;
}

.video-card:hover .v-play-ring {
  box-shadow: 0 0 36px rgba(201, 75, 40, 0.8);
}

.v-play svg {
  position: relative;
  z-index: 1;
  margin-left: 2px;
}

/* Top accent line */
.v-accent-line {
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 2px;
  background: linear-gradient(to right, var(--accent), var(--accent2));
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.4s cubic-bezier(0.22, 1, 0.36, 1);
  z-index: 5;
}

.video-card:hover .v-accent-line {
  transform: scaleX(1);
}
</style>
