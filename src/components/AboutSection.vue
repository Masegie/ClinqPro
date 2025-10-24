<template>
  <section id="about" class="bg-white">
    <div class="section-wrapper space-y-14 md:space-y-20">
      <div
        class="mx-auto w-full max-w-[1400px] rounded-[2.5rem] bg-white px-8 py-12 shadow-sm ring-1 ring-gray-100 md:px-14 md:py-16"
      >
        <div
          class="grid gap-10 md:grid-cols-[minmax(0,0.8fr)_minmax(0,1fr)] md:items-center"
        >
          <div>
            <p class="text-xs uppercase tracking-[0.5em] text-gray-400">
              Why Clinq Pro
            </p>
            <h2 class="mt-4 text-3xl font-semibold text-gray-900 md:text-4xl">
              Redefining clean with purpose and precision
            </h2>
            <div
              class="mt-6 inline-flex items-center gap-2 rounded-2xl bg-gray-100 px-4 py-2 text-sm font-medium text-gray-600"
            >
              <span>Trusted for top-to-bottom refresh</span>
            </div>
          </div>
          <p class="text-sm leading-relaxed text-gray-500 md:text-base md:text-right">
            Brings modern, fast-drying, door-to-door cleaning at affordable
            prices, ensuring maximum results with ease. Clinq Pro combines
            eco-friendly methods with professional care so every clean feels
            like a reset.
          </p>
        </div>

        <div class="mt-12 grid grid-cols-1 gap-6 md:grid-cols-3">
        <!-- Card 1 -->
        <article
          v-reveal
          class="flex h-full flex-col rounded-[2rem] border border-gray-200 bg-white p-6 text-left shadow-sm transition hover:-translate-y-1 hover:shadow-lg"
        >
          <div
            class="relative overflow-hidden rounded-[1.5rem] border border-[#C8DAFF] bg-[#F3F6FF] p-4"
          >
            <img
              src="@/assets/images/about-door.png"
              alt="Door to door service"
              class="h-48 w-full rounded-[1.25rem] object-cover md:h-56"
              loading="lazy"
              decoding="async"
            />
          </div>
          <div class="mt-6 flex flex-col gap-4">
            <p class="text-base leading-relaxed text-gray-700">
              We come directly to your place with fast service and outstanding
              results.
            </p>
            <div>
              <span
                class="inline-flex items-center rounded-full bg-gray-100 px-3 py-1 text-xs font-medium text-gray-600"
              >
                Door-to-door
              </span>
            </div>
          </div>
        </article>

        <!-- Card 2 -->
        <article
          v-reveal="{ delay: 80 }"
          class="flex h-full flex-col rounded-[2rem] border border-gray-200 bg-white p-6 text-left shadow-sm transition hover:-translate-y-1 hover:shadow-lg"
        >
          <div
            class="relative overflow-hidden rounded-[1.5rem] border border-[#C8DAFF] bg-[#F3F6FF] p-4"
          >
            <img
              src="@/assets/images/about-modern.png"
              alt="Modern technology"
              class="h-48 w-full rounded-[1.25rem] object-cover md:h-56"
              loading="lazy"
              decoding="async"
            />
          </div>
          <div class="mt-6 flex flex-col gap-4">
            <p class="text-base leading-relaxed text-gray-700">
              Modern technology ensures your furnishings and spaces are clean,
              hygienic, and comfortable.
            </p>
            <div>
              <span
                class="inline-flex items-center rounded-full bg-gray-100 px-3 py-1 text-xs font-medium text-gray-600"
              >
                Modern
              </span>
            </div>
          </div>
        </article>

        <!-- Card 3 -->
        <article
          v-reveal="{ delay: 160 }"
          class="flex h-full flex-col rounded-[2rem] border border-gray-200 bg-white p-6 text-left shadow-sm transition hover:-translate-y-1 hover:shadow-lg"
        >
          <div
            class="relative overflow-hidden rounded-[1.5rem] border border-[#C8DAFF] bg-[#F3F6FF] p-4"
          >
            <img
              src="@/assets/images/about-affordable.png"
              alt="Affordable service"
              class="h-48 w-full rounded-[1.25rem] object-cover md:h-56"
              loading="lazy"
              decoding="async"
            />
          </div>
          <div class="mt-6 flex flex-col gap-4">
            <p class="text-base leading-relaxed text-gray-700">
              At affordable prices, we serve both individuals and businesses
              with ease.
            </p>
            <div>
              <span
                class="inline-flex items-center rounded-full bg-gray-100 px-3 py-1 text-xs font-medium text-gray-600"
              >
                Affordable
              </span>
            </div>
          </div>
        </article>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
// simple reveal directive (local)
const vReveal = {
  mounted(el, binding) {
    // respect prefers-reduced-motion
    if (window.matchMedia("(prefers-reduced-motion: reduce)").matches) {
      el.style.opacity = 1;
      el.style.transform = "none";
      return;
    }
    const dy = binding?.value?.y ?? 20;
    const delay = binding?.value?.delay ?? 0;
    el.style.opacity = 0;
    el.style.transform = `translateY(${dy}px)`;
    const io = new IntersectionObserver(
      ([e]) => {
        if (e.isIntersecting) {
          setTimeout(() => {
            el.style.transition =
              "opacity 600ms cubic-bezier(.2,.6,.2,1), transform 600ms cubic-bezier(.2,.6,.2,1)";
            el.style.opacity = 1;
            el.style.transform = "translateY(0)";
          }, delay);
          io.unobserve(el);
        }
      },
      { threshold: 0.25 }
    );
    io.observe(el);
  },
};
</script>
