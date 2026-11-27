<script setup>
import { ref, watch } from 'vue'

const props = defineProps({
  src: { type: String, default: '' },
  label: { type: String, default: 'GIF' },
  code: { type: String, default: 'CH-00' },
  ratio: { type: String, default: '16 / 9' },
})

const failed = ref(false)
watch(() => props.src, () => (failed.value = false))
</script>

<template>
  <figure class="gif-slot" :style="{ aspectRatio: ratio }">
    <img v-if="src && !failed" :src="src" :alt="label" loading="lazy" @error="failed = true" />
    <div v-else class="placeholder" aria-hidden="true">
      <div class="static"></div>
      <span class="ph-title">NO SIGNAL</span>
      <span class="ph-label">{{ label }}</span>
    </div>
    <figcaption>
      <span>{{ code }}</span>
      <span class="rec">● REC</span>
    </figcaption>
    <i class="corner tl"></i><i class="corner tr"></i><i class="corner bl"></i><i class="corner br"></i>
  </figure>
</template>

<style scoped>
.gif-slot {
  position: relative;
  margin: 0;
  width: 100%;
  overflow: hidden;
  background: #0b0b12;
  border: 1px solid var(--line);
  isolation: isolate;
}

.gif-slot img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  filter: saturate(1.15) contrast(1.05);
}

.gif-slot::after {
  content: '';
  position: absolute;
  inset: 0;
  pointer-events: none;
  background: repeating-linear-gradient(0deg, rgba(0, 0, 0, 0.28) 0 1px, transparent 1px 3px);
  mix-blend-mode: multiply;
  z-index: 2;
}

.placeholder {
  position: absolute;
  inset: 0;
  display: grid;
  place-content: center;
  text-align: center;
  gap: 6px;
  font-family: var(--mono);
  color: var(--muted);
}

.static {
  position: absolute;
  inset: -50%;
  opacity: 0.12;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='160' height='160'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.9' numOctaves='2' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
  animation: static 0.4s steps(4) infinite;
  z-index: -1;
}

@keyframes static {
  0% { transform: translate(0, 0); }
  25% { transform: translate(-6%, 4%); }
  50% { transform: translate(5%, -3%); }
  75% { transform: translate(-3%, -6%); }
  100% { transform: translate(0, 0); }
}

.ph-title {
  font-family: var(--display);
  font-size: clamp(1.4rem, 3vw, 2.4rem);
  letter-spacing: 0.12em;
  color: var(--red);
  text-shadow: 2px 0 var(--cyan), -2px 0 var(--red);
}

.ph-label {
  font-size: 0.75rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
}

figcaption {
  position: absolute;
  left: 10px;
  right: 10px;
  bottom: 8px;
  display: flex;
  justify-content: space-between;
  font-family: var(--mono);
  font-size: 0.7rem;
  letter-spacing: 0.15em;
  color: var(--ink);
  z-index: 3;
  text-shadow: 0 0 6px #000;
}

.rec {
  color: var(--red);
  animation: blink 1.2s steps(2) infinite;
}

@keyframes blink {
  50% { opacity: 0; }
}

.corner {
  position: absolute;
  width: 14px;
  height: 14px;
  border: 2px solid var(--cyan);
  z-index: 3;
}
.tl { top: 6px; left: 6px; border-right: 0; border-bottom: 0; }
.tr { top: 6px; right: 6px; border-left: 0; border-bottom: 0; }
.bl { bottom: 26px; left: 6px; border-right: 0; border-top: 0; }
.br { bottom: 26px; right: 6px; border-left: 0; border-top: 0; }

@media (prefers-reduced-motion: reduce) {
  .static, .rec { animation: none; }
}
</style>
