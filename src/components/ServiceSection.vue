<template>
  <section id="service" class="bg-gray-50">
    <div class="section-wrapper text-center">
      <div
        class="mx-auto w-full max-w-[1400px] rounded-[2rem] bg-white/80 px-8 py-14 text-center shadow-sm backdrop-blur"
      >
        <p class="text-sm uppercase tracking-wide text-gray-400">
          Service and Pricing
        </p>
        <h2 class="mt-4 text-3xl font-medium text-gray-700 md:text-4xl">
          We offer
          <span class="font-semibold text-gray-900">Quality</span>
          and
          <span class="font-semibold text-gray-900">Affordable</span>
          price
        </h2>
        <div
          class="mt-6 inline-flex items-center gap-2 rounded-full bg-gray-100 px-5 py-3 text-sm font-medium text-gray-700 shadow-sm"
        >
          <span>Start from</span>
          <span class="font-semibold text-gray-900">35K</span>
          <span>!</span>
        </div>
      </div>
      <div class="relative mt-12">
        <div
          ref="slider"
          class="group overflow-hidden pb-3"
          @mouseenter="stopMarquee"
          @mouseleave="startMarquee"
        >
          <div class="flex w-max gap-6">
            <article
              v-for="service in services"
              :key="service.id"
              class="flex w-[240px] flex-shrink-0 flex-col rounded-3xl border border-gray-200 bg-white p-6 text-left shadow-sm transition hover:-translate-y-1 hover:shadow-lg sm:w-[260px] lg:w-[280px]"
            >
              <div
                class="relative mb-6 flex h-40 items-center justify-center overflow-hidden rounded-2xl bg-gray-50"
              >
                <img
                  :src="service.image"
                  :alt="service.title"
                  class="h-full w-full object-contain"
                />
              </div>

              <h3 class="text-lg font-semibold text-gray-900">
                {{ service.title }}
              </h3>
              <p class="mt-2 text-sm text-gray-500">{{ service.subtitle }}</p>
              <div class="mt-3 flex items-center justify-between">
                <p class="text-base font-semibold text-gray-900">
                  {{ service.price }}
                </p>
                <button
                  type="button"
                  class="grid h-10 w-10 place-items-center rounded-xl bg-gray-100 text-lg font-semibold text-gray-500 transition hover:bg-gray-200 hover:text-gray-700"
                >
                  &gt;
                </button>
              </div>
            </article>
          </div>
        </div>
      </div>

      <p class="mt-16 text-center text-2xl font-medium text-gray-600 md:text-3xl">
        We also provide exclusive packages for organizations, with flexible
        pricing designed just for you.
      </p>
    </div>
  </section>
</template>

<script setup>
import { nextTick, onBeforeUnmount, onMounted, ref } from "vue";

const baseServices = Array.from({ length: 10 }, (_, index) => ({
  id: index + 1,
  title: "Baby Stuff Cleaning",
  subtitle: "From",
  price: "Rp 45.000/m²",
  image: new URL(
    "@/assets/images/beforeafter/carpet-after.png",
    import.meta.url
  ).href,
}));

const services = baseServices.flatMap((service) => [
  service,
  {
    ...service,
    id: `${service.id}-clone`,
  },
]);

const slider = ref(null);
let animationId = null;
const speed = 0.4;

const step = () => {
  const container = slider.value;
  if (!container) {
    animationId = null;
    return;
  }

  container.scrollLeft += speed;
  const halfScrollWidth = container.scrollWidth / 2;

  if (halfScrollWidth > 0 && container.scrollLeft >= halfScrollWidth) {
    container.scrollLeft -= halfScrollWidth;
  }

  animationId = requestAnimationFrame(step);
};

const startMarquee = () => {
  if (!animationId) {
    animationId = requestAnimationFrame(step);
  }
};

const stopMarquee = () => {
  if (animationId) {
    cancelAnimationFrame(animationId);
    animationId = null;
  }
};

const handleResize = () => {
  const container = slider.value;
  if (!container) {
    return;
  }

  const halfScrollWidth = container.scrollWidth / 2;
  if (halfScrollWidth > 0) {
    container.scrollLeft = container.scrollLeft % halfScrollWidth;
  }
};

onMounted(() => {
  nextTick(() => {
    const container = slider.value;
    if (container) {
      container.scrollLeft = 0;
    }
    startMarquee();
  });

  window.addEventListener("resize", handleResize);
});

onBeforeUnmount(() => {
  stopMarquee();
  window.removeEventListener("resize", handleResize);
});
</script>
