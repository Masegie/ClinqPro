<template>
  <section class="bg-white py-24">
    <div
      class="section-wrapper flex flex-col gap-12 rounded-3xl bg-gray-100/80 px-8 py-10 md:flex-row md:items-center md:gap-16 md:px-14 md:py-12"
    >
      <div class="flex flex-col items-center text-center md:w-1/3 md:text-left">
        <div
          class="mb-6 h-32 w-32 overflow-hidden rounded-full border-4 border-white shadow-md"
        >
          <img
            :src="profile.image"
            :alt="`Foto ${profile.name}`"
            class="h-full w-full object-cover"
          />
        </div>
        <h3 class="text-2xl font-semibold text-gray-900">
          {{ profile.name }}
        </h3>
        <p class="mt-1 text-sm text-gray-500">{{ profile.role }}</p>
      </div>

      <blockquote class="md:w-2/3">
        <span class="text-4xl font-semibold text-gray-400">“</span>
        <p class="inline text-lg leading-relaxed text-gray-700 md:text-xl">
          Eh pas coba jasa
          <a
            href="https://www.instagram.com/clinqpro"
            target="_blank"
            rel="noopener"
            class="font-semibold text-[#2CA59D]"
          >
            @clinqpro
          </a>
          ini ternyata beda banget. Prosesnya cuma sejam, blowernya nggak perlu
          ditinggal, sofa langsung kering dan bisa langsung dipakai duduk lagi.
          Nggak perlu kipas, AC, atau sewa blower seharian kayak biasanya.
        </p>
        <p class="mt-4 text-lg leading-relaxed text-gray-700 md:text-xl">
          Buat aku ini sih beneran life saver banget. Jadi kalau mau cuci sofa,
          karpet, atau jasa cleaning lainnya, aku udah tau jawabannya kemana.
        </p>
      </blockquote>
    </div>
  </section>
</template>

<script setup>
const profile = {
  name: "Rumah.imnd",
  role: "Content Creator",
  image: new URL("@/assets/images/about-modern.png", import.meta.url).href,
};
</script>
