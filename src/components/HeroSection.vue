<template>
  <section
    id="home"
    ref="heroSection"
    class="relative w-full min-h-[100vh] flex items-start bg-white"
  >
    <div class="section-wrapper pt-6 sm:pt-8 md:pt-10">
      <div class="relative w-full overflow-hidden rounded-[2rem]">
        <div
          class="relative mx-auto w-full max-w-[1400px] overflow-hidden rounded-[2rem]"
        >
          <!-- LAYER 1: base (statis) -->
          <img
            src="@/assets/images/hero-cleaning-base.png"
            alt="Cleaning Base"
            class="block h-[82vh] w-full min-h-[480px] object-cover object-center pointer-events-none select-none sm:min-h-[560px] md:min-h-[640px]"
          />

          <!-- LAYER 2: teks (parallax only di teks) -->
          <div
            class="absolute left-1/2 top-1/2 z-[1] text-center transition-all duration-700 ease-out"
            :style="{
              transform: `translate(-50%, calc(-${offsetY * 0.3}px - 120%))`,
              opacity: textOpacity,
              filter: `blur(${textBlur}px)`,
            }"
          >
            <h1
              class="px-4 text-[clamp(2.8rem,8vw,11rem)] font-extrabold leading-[1.02] tracking-tight select-none text-left bg-gradient-to-br from-[#274940] to-[#5DAF9A] text-transparent bg-clip-text drop-shadow-lg sm:px-8"
            >
              The&nbsp;Ultimate <br />
              Cleaning&nbsp;Hero
            </h1>
          </div>

          <!-- LAYER 3: hero utama (statis, di depan teks) -->
          <img
            src="@/assets/images/hero-cleaning.png"
            alt="Cleaning Hero"
            class="absolute inset-0 z-[2] block h-[82vh] w-full min-h-[480px] object-cover object-center pointer-events-none select-none sm:min-h-[560px] md:min-h-[640px]"
          />
          <!-- LAYER 4: cards – nempel kanan-bawah, horizontal -->
          <div
            class="absolute bottom-6 left-1/2 z-[3] w-[min(90vw,340px)] -translate-x-1/2 px-3 sm:w-[min(85vw,420px)] sm:px-4 md:bottom-[6%] md:left-auto md:right-[6%] md:w-auto md:max-w-[660px] md:translate-x-0 md:transform-none"
          >
            <StatsCard />
          </div>
        </div>
      </div>
    </div>
    <!-- wrapper pakai container sama seperti navbar -->
  </section>
</template>

<script setup>
import { ref, onMounted } from "vue";
import StatsCard from "@/components/StatsCard.vue";

const offsetY = ref(0);
const textOpacity = ref(0);
const textBlur = ref(10);

let targetY = 0;
const smoothScroll = () => {
  targetY += (window.scrollY - targetY) * 0.1;
  offsetY.value = targetY;
  requestAnimationFrame(smoothScroll);
};

onMounted(() => {
  requestAnimationFrame(smoothScroll);
  setTimeout(() => {
    textOpacity.value = 1;
    textBlur.value = 0;
  }, 300);
});
</script>

<style scoped>
section {
  perspective: 1000px;
}
</style>
