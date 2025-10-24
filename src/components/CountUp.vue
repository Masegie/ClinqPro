<template>
  <span ref="root">{{ display }}</span>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const props = defineProps({
  end: { type: Number, required: true }, // angka tujuan
  start: { type: Number, default: 0 }, // mulai dari
  duration: { type: Number, default: 1200 }, // ms
  decimals: { type: Number, default: 0 }, // jumlah desimal
  prefix: { type: String, default: "" },
  suffix: { type: String, default: "" },
  easing: { type: Boolean, default: true },
  once: { type: Boolean, default: true }, // animasi sekali saja
});

const root = ref(null);
const display = ref("");
let started = false;
let rafId = 0;
let observer;

const fmt = (n) =>
  n.toLocaleString(undefined, {
    minimumFractionDigits: props.decimals,
    maximumFractionDigits: props.decimals,
  });

const easeOutCubic = (t) => 1 - Math.pow(1 - t, 3);

function start() {
  if (started && props.once) return;
  started = true;

  const from = props.start;
  const to = props.end;
  const t0 = performance.now();

  const tick = (now) => {
    const raw = Math.min((now - t0) / props.duration, 1);
    const p = props.easing ? easeOutCubic(raw) : raw;
    const current = from + (to - from) * p;
    display.value = `${props.prefix}${fmt(current)}${props.suffix}`;
    if (raw < 1) rafId = requestAnimationFrame(tick);
  };

  rafId = requestAnimationFrame(tick);
}

onMounted(() => {
  display.value = `${props.prefix}${fmt(props.start)}${props.suffix}`;
  observer = new IntersectionObserver(
    ([entry]) => {
      if (entry.isIntersecting) start();
    },
    { threshold: 0.4 }
  );
  observer.observe(root.value);
});

onUnmounted(() => {
  cancelAnimationFrame(rafId);
  observer && observer.disconnect();
});
</script>
