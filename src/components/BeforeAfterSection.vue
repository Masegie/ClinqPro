<template>
  <section id="beforeafter" class="bg-gray-50">
    <div class="section-wrapper">
      <div
        class="mx-auto w-full max-w-[1400px] rounded-[2.5rem] bg-white px-8 py-12 text-center shadow-sm ring-1 ring-gray-100 md:px-14 md:py-16"
      >
        <div class="mx-auto max-w-4xl">
          <p class="text-xs uppercase tracking-[0.45em] text-gray-400">
            Transformation Stories
          </p>
          <h2 class="mt-4 text-3xl font-medium text-gray-900 md:text-4xl">
            See the difference before and after Clinq Pro
          </h2>
          <p class="mt-4 text-sm text-gray-500 md:text-base">
            Each swipe reveals how our deep cleaning brings back freshness and
            comfort to every surface we touch.
          </p>
        </div>

        <!-- SLIDER UTAMA -->
        <div
          class="mx-auto mt-12 w-full max-w-[1100px] rounded-[2rem] bg-white p-4 shadow-md"
        >
          <BeforeAfterSlider :before="current.before" :after="current.after" />
        </div>

        <!-- THUMBNAILS -->
        <div class="mt-10 flex flex-wrap justify-center gap-3">
          <button
            v-for="(item, i) in images"
            :key="i"
            @click="current = item"
            class="h-16 w-16 overflow-hidden rounded-xl border-2 transition sm:h-[72px] sm:w-[72px] md:h-[90px] md:w-[90px]"
            :class="
              current.before === item.before
                ? 'border-[#2CA59D]'
                : 'border-transparent'
            "
          >
            <div class="relative h-full w-full">
              <img
                :src="item.before"
                alt="thumb before"
                class="absolute inset-0 h-full w-full object-cover opacity-90"
              />
              <img
                :src="item.after"
                alt="thumb after"
                class="absolute inset-0 h-full w-full object-cover mix-blend-overlay opacity-90"
              />
            </div>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";
import BeforeAfterSlider from "./BeforeAfterSlider.vue";

const images = [
  {
    before: new URL(
      "@/assets/images/beforeafter/sofa-before.png",
      import.meta.url
    ).href,
    after: new URL(
      "@/assets/images/beforeafter/sofa-after.png",
      import.meta.url
    ).href,
  },
  {
    before: new URL(
      "@/assets/images/beforeafter/toilet-before.png",
      import.meta.url
    ).href,
    after: new URL(
      "@/assets/images/beforeafter/toilet-after.png",
      import.meta.url
    ).href,
  },
  {
    before: new URL(
      "@/assets/images/beforeafter/mattress-before.png",
      import.meta.url
    ).href,
    after: new URL(
      "@/assets/images/beforeafter/mattress-after.png",
      import.meta.url
    ).href,
  },
  {
    before: new URL(
      "@/assets/images/beforeafter/chair-before.png",
      import.meta.url
    ).href,
    after: new URL(
      "@/assets/images/beforeafter/chair-after.png",
      import.meta.url
    ).href,
  },
  {
    before: new URL(
      "@/assets/images/beforeafter/carpet-before.png",
      import.meta.url
    ).href,
    after: new URL(
      "@/assets/images/beforeafter/carpet-after.png",
      import.meta.url
    ).href,
  },
];

const current = ref(images[0]);
</script>
