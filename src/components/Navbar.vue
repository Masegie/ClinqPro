<template>
  <header class="fixed top-0 left-0 w-full z-50 bg-white/70 backdrop-blur-md">
    <div
      class="container mx-auto flex items-center justify-between px-5 py-3 sm:px-8 md:px-12 xl:px-16 md:py-4"
    >
      <!-- Logo -->
      <div class="flex items-center space-x-2">
        <img :src="logo" alt="Clinq Pro Logo" class="h-12" />
      </div>

      <!-- Navigation Pills -->
      <nav class="hidden md:flex items-center bg-gray-100 rounded-xl px-2 py-2">
        <button
          v-for="link in links"
          :key="link.name"
          type="button"
          @click="handleNavClick(link)"
          class="relative flex items-center px-5 py-2.5 rounded-xl text-[15px] font-medium transition-all duration-200 outline-none focus:outline-none"
          :class="{
            'bg-white text-[#184D47] shadow-sm': activeLink === link.name,
            'text-gray-800 hover:text-[#184D47]': activeLink !== link.name,
          }"
        >
          <!-- Green Dot Indicator -->
          <span
            v-if="activeLink === link.name"
            class="mr-2 w-2 h-2 bg-[#2CA59D] rounded-full"
          ></span>
          {{ link.name }}
        </button>
      </nav>

      <!-- Contact Button -->
      <div class="flex items-center gap-3">
        <a
          href="#contact"
          @click.prevent="goToContact"
          class="hidden md:inline-flex bg-[#2CA59D] text-white px-5 py-2 rounded-full hover:bg-[#21847f] transition"
        >
          Contact Us →
        </a>
        <button
          type="button"
          class="inline-flex h-11 w-11 items-center justify-center rounded-full border border-gray-200 text-gray-600 transition hover:bg-gray-100 md:hidden"
          @click="toggleMenu"
          aria-label="Toggle navigation"
        >
          <svg
            v-if="!isMenuOpen"
            class="h-6 w-6"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="1.8"
            stroke-linecap="round"
          >
            <path d="M4 7h16" />
            <path d="M4 12h16" />
            <path d="M4 17h16" />
          </svg>
          <svg
            v-else
            class="h-6 w-6"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="1.8"
            stroke-linecap="round"
          >
            <path d="M6 6l12 12" />
            <path d="M18 6l-12 12" />
          </svg>
        </button>
      </div>
    </div>

    <!-- Mobile menu -->
    <transition
      enter-active-class="duration-200 ease-out"
      enter-from-class="opacity-0"
      enter-to-class="opacity-100"
      leave-active-class="duration-150 ease-in"
      leave-from-class="opacity-100"
      leave-to-class="opacity-0"
    >
      <div
        v-if="isMenuOpen"
        class="md:hidden fixed inset-0 z-40 bg-black/30 backdrop-blur-sm"
        @click.self="closeMenu"
      >
        <nav
          class="absolute left-4 right-4 top-20 space-y-3 rounded-2xl bg-white/95 p-4 shadow-xl ring-1 ring-gray-100"
        >
          <button
            v-for="link in links"
            :key="link.name"
            type="button"
            @click="handleNavClick(link)"
            class="flex w-full items-center justify-between rounded-xl px-4 py-3 text-base font-medium text-gray-700 transition hover:bg-gray-100"
          >
            <span>{{ link.name }}</span>
            <span
              class="text-sm font-semibold text-[#2CA59D]"
              aria-hidden="true"
            >
              →
            </span>
          </button>
          <a
            href="#contact"
            @click.prevent="goToContact"
            class="mt-2 block rounded-xl bg-[#2CA59D] px-4 py-3 text-center text-base font-semibold text-white transition hover:bg-[#21847f]"
          >
            Contact Us
          </a>
        </nav>
      </div>
    </transition>
  </header>
</template>

<script setup>
import { ref, watch, onBeforeUnmount } from "vue";
import logo from "@/assets/logo.png";

const links = [
  { name: "Home", href: "#home" },
  { name: "About Us", href: "#about" },
  { name: "Service & Pricing", href: "#service" },
  { name: "Testimonies", href: "#testimonies" },
];

const activeLink = ref("Home");
const isMenuOpen = ref(false);

function handleNavClick(link) {
  activeLink.value = link.name;
  scrollToSection(link.href);
  closeMenu();
}

function scrollToSection(selector) {
  if (typeof window === "undefined") {
    return;
  }

  const target = document.querySelector(selector);
  if (!target) {
    return;
  }

  const header = document.querySelector("header");
  const headerOffset = header ? header.offsetHeight + 16 : 0;
  const elementPosition =
    target.getBoundingClientRect().top + window.scrollY - headerOffset;

  window.scrollTo({
    top: Math.max(elementPosition, 0),
    behavior: "smooth",
  });
}

function toggleMenu() {
  isMenuOpen.value = !isMenuOpen.value;
}

function closeMenu() {
  isMenuOpen.value = false;
}

function goToContact() {
  scrollToSection("#contact");
  closeMenu();
}

watch(isMenuOpen, (open) => {
  if (typeof document === "undefined") return;
  document.body.classList.toggle("overflow-hidden", open);
});

onBeforeUnmount(() => {
  if (typeof document === "undefined") return;
  document.body.classList.remove("overflow-hidden");
});
</script>
