<template>
  <footer
    id="contact"
    class="bg-gradient-to-b from-[#1d7a72] via-[#166560] to-[#0f4b47] text-white"
  >
    <div class="section-wrapper py-20">
      <div class="space-y-12">
        <div
          class="inline-flex items-center gap-2 rounded-full bg-white/10 px-4 py-2 text-sm text-white/80 shadow-sm backdrop-blur-sm"
        >
          <span class="text-lg" aria-hidden="true">📍</span>
          <span>Bogor, Indonesia</span>
        </div>

        <div class="space-y-4">
          <h2 class="text-3xl font-medium text-white md:text-4xl">
            Let’s create cleaner,<br class="md:hidden" />
            healthier spaces—together.
          </h2>
        </div>

        <hr class="border-white/30" />

        <div class="grid gap-12 md:grid-cols-4">
          <div>
            <h3 class="text-sm uppercase tracking-wide text-white/70">
              Address
            </h3>
            <p class="mt-4 text-lg leading-relaxed text-white/90">
              Jl. Griya Laladon Grande C3, Laladon, Ciomas,<br />
              Bogor Regency, West Java 16610.
            </p>
          </div>

          <div>
            <h3 class="text-sm uppercase tracking-wide text-white/70">
              Phone / Whatsapp
            </h3>
            <a
              href="https://wa.me/6285117076820"
              target="_blank"
              rel="noopener"
              class="mt-4 inline-flex items-center gap-2 text-lg font-semibold text-white underline underline-offset-4 hover:text-[#D1FFF6]"
            >
              +62 851-1707-6820
              <span aria-hidden="true">↗</span>
            </a>
          </div>

          <div>
            <h3 class="text-sm uppercase tracking-wide text-white/70">
              Email
            </h3>
            <a
              href="mailto:clinqpro@gmail.com"
              class="mt-4 block text-lg leading-relaxed text-white/90 hover:text-white"
            >
              clinqpro@gmail.com
            </a>
          </div>

          <div>
            <h3 class="text-sm uppercase tracking-wide text-white/70">
              Social Media
            </h3>
            <a
              href="https://www.instagram.com/clinqpro"
              target="_blank"
              rel="noopener"
              class="mt-4 inline-flex items-center gap-2 text-lg leading-relaxed text-white/90 hover:text-white"
            >
              @clinqpro
              <span aria-hidden="true">↗</span>
            </a>
          </div>
        </div>
      </div>
    </div>
    <div class="border-t border-white/20 py-6 text-center text-sm text-white/70">
      © {{ new Date().getFullYear() }} Clinq Pro. All rights reserved.
    </div>
  </footer>
</template>
