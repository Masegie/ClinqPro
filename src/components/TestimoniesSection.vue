<template>
  <section id="testimonies" class="bg-white">
    <div class="section-wrapper">
      <div class="mx-auto max-w-3xl text-center">
        <p class="text-sm uppercase tracking-[0.4em] text-gray-400">
          Testimonials
        </p>
        <h2 class="mt-4 text-3xl font-medium text-gray-900 md:text-4xl">
          What our customers say about ClinqPro
        </h2>
        <p class="mt-4 text-base text-gray-500 md:text-lg">
          Mereka puas dengan hasil pembersihan kami yang cepat, rapi, dan
          ramah—kami pastikan rumah terasa nyaman kembali.
        </p>
        <div
          class="mt-12 flex flex-col gap-8 rounded-3xl border border-gray-100 bg-gray-50 p-8 text-left shadow-sm md:flex-row md:items-center md:gap-10"
        >
          <div
            class="flex flex-col items-center text-center md:w-[240px] md:items-center"
          >
            <div
              class="h-24 w-24 overflow-hidden rounded-full border-4 border-white shadow-md"
            >
              <img
                :src="featuredHighlight.avatar"
                :alt="`Foto ${featuredHighlight.author}`"
                class="h-full w-full object-cover"
              />
            </div>
            <h3 class="mt-4 text-xl font-semibold text-gray-900">
              {{ featuredHighlight.author }}
            </h3>
            <p class="text-sm text-gray-500">{{ featuredHighlight.role }}</p>
          </div>

          <div class="md:flex-1 md:text-left">
            <p class="text-base leading-relaxed text-gray-700 md:text-lg">
              “{{ featuredHighlight.beforeHandle }}
              <a
                href="https://www.instagram.com/clinqpro"
                target="_blank"
                rel="noopener"
                class="font-semibold text-[#2CA59D]"
              >
                @clinqpro
              </a>
              {{ featuredHighlight.afterHandle }}”
            </p>
            <p class="mt-4 text-base leading-relaxed text-gray-700 md:text-lg">
              {{ featuredHighlight.second }}
            </p>
          </div>
        </div>
      </div>

      <div class="mt-16 grid gap-8 md:grid-cols-3">
        <article
          v-for="(item, index) in testimonies"
          :key="item.name"
          class="flex h-full flex-col justify-between rounded-3xl border border-gray-100 bg-gray-50/60 p-8 text-left shadow-sm transition hover:-translate-y-1 hover:shadow-lg"
        >
          <div>
            <div class="flex items-center gap-3">
              <div
                class="flex h-12 w-12 items-center justify-center rounded-full bg-[#2CA59D]/10 text-lg font-semibold text-[#2CA59D]"
              >
                {{ item.initials }}
              </div>
              <div>
                <h3 class="text-lg font-semibold text-gray-900">
                  {{ item.name }}
                </h3>
                <p class="text-sm text-gray-500">{{ item.role }}</p>
              </div>
            </div>

            <p class="mt-6 text-base leading-relaxed text-gray-600 md:text-lg">
              “{{ item.quote }}”
            </p>
          </div>

          <div class="mt-8 flex items-center gap-1 text-[#2CA59D]" aria-hidden="true">
            <span v-for="star in 5" :key="`${index}-${star}`">★</span>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
const featuredHighlight = {
  beforeHandle: "Eh pas coba jasa",
  afterHandle:
    "ini ternyata beda banget. Prosesnya cuma sejam, blowernya nggak perlu ditinggal, sofa langsung kering dan bisa langsung dipakai duduk lagi. Nggak perlu kipas, AC, atau sewa blower seharian kayak biasanya.",
  second:
    "Buat aku ini sih beneran life saver banget. Jadi kalau mau cuci sofa, karpet, atau jasa cleaning lainnya, aku udah tau jawabannya kemana.",
  author: "Rumah.imnd",
  role: "Content Creator",
  avatar: new URL("@/assets/images/about-modern.png", import.meta.url).href,
};

const testimonies = [
  {
    name: "Rani - Jakarta",
    role: "Ibu Rumah Tangga",
    quote:
      "Sofanya langsung bersih dan wangi. Anak-anak bisa langsung pakai tanpa khawatir karena keringnya cepat banget!",
    initials: "RJ",
  },
  {
    name: "Arif - Bekasi",
    role: "Karyawan Swasta",
    quote:
      "Timnya tepat waktu, pengerjaannya rapi, dan hasilnya di atas ekspektasi. Worth it banget untuk jasa cuci sofa rutin.",
    initials: "AB",
  },
  {
    name: "Nina - Tangerang",
    role: "Pemilik Coffee Shop",
    quote:
      "ClinqPro bantu jaga kebersihan kursi kafe saya. Pelanggan sering bilang kursinya terasa fresh dan nyaman.",
    initials: "NT",
  },
];
</script>
