<template>
  <div
    class="w-full max-w-[680px] rounded-3xl bg-white/25 p-3 shadow-[0_20px_40px_rgba(18,18,18,0.12)] backdrop-blur-xl sm:w-fit"
  >
    <div
      class="grid gap-3 sm:grid-flow-col sm:auto-cols-fr sm:items-center sm:gap-4"
    >
      <div
        v-for="s in stats"
        :key="s.label"
        class="rounded-2xl bg-white px-5 py-4 text-center shadow-[0_12px_28px_rgba(15,76,69,0.16)] transition-transform duration-200 hover:-translate-y-0.5 hover:shadow-[0_16px_36px_rgba(15,76,69,0.18)] sm:min-w-[160px] sm:px-7 sm:py-5"
      >
        <h3 class="text-2xl font-extrabold text-gray-900 sm:text-3xl">
          <CountUp :end="s.end" :suffix="s.suffix || ''" :duration="1100" />
        </h3>
        <p class="mt-1 text-xs text-gray-600 sm:text-sm">{{ s.label }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import CountUp from "@/components/CountUp.vue";

const stats = [
  { end: 11, label: "Total Service" },
  { end: 90, suffix: "+", label: "Customers Served" },
  { end: 100, suffix: " %", label: "Happy Customers" },
];
</script>
