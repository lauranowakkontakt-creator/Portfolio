<template>
  <Teleport to="body">
    <div class="modal-backdrop" @click.self="$emit('close')" @keydown.esc="$emit('close')">
      <div class="modal-box" :class="{ 'modal-short': isShort }">
        <button class="modal-close" @click="$emit('close')" aria-label="Zamknij">
          <svg viewBox="0 0 24 24" width="20" height="20" fill="none" stroke="currentColor" stroke-width="2">
            <line x1="18" y1="6" x2="6" y2="18"/>
            <line x1="6" y1="6" x2="18" y2="18"/>
          </svg>
        </button>
        <div class="embed-wrap">
          <iframe
            :src="`https://www.youtube.com/embed/${videoId}?autoplay=1&rel=0`"
            frameborder="0"
            allow="autoplay; encrypted-media; fullscreen"
            allowfullscreen
          />
        </div>
      </div>
    </div>
  </Teleport>
</template>

<script setup>
const props = defineProps({
  videoId: { type: String, required: true },
  isShort: { type: Boolean, default: false },
})
defineEmits(['close'])
</script>

<style scoped>
.modal-backdrop {
  position: fixed;
  inset: 0;
  z-index: 200;
  background: rgba(0, 0, 0, 0.88);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1.5rem;
  backdrop-filter: blur(6px);
}

.modal-box {
  position: relative;
  width: 100%;
  max-width: 960px;
}

.modal-close {
  position: absolute;
  top: -2.8rem;
  right: 0;
  background: none;
  border: none;
  color: rgba(242, 240, 237, 0.6);
  cursor: pointer;
  padding: 0.4rem;
  transition: color 0.2s;
  display: flex;
}

.modal-close:hover {
  color: var(--text);
}

.embed-wrap {
  position: relative;
  width: 100%;
  padding-bottom: 56.25%;
}

.modal-short .embed-wrap {
  padding-bottom: 177.78%;
}

.embed-wrap iframe {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
}

.modal-short {
  max-width: 380px;
}
</style>
