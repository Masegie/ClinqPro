<template>
  <div class="bg-white">
    <Navbar />
    <main class="pt-[4.25rem] md:pt-[4.75rem] lg:pt-[5rem]">
      <HeroSection />
      <AboutSection />
      <BeforeAfterSection />
      <ServiceSection />
      <TestimoniesSection />
      <FooterSection />
    </main>
  </div>
</template>

<script setup>
import Navbar from "./components/Navbar.vue";
import HeroSection from "./components/HeroSection.vue";
import AboutSection from "./components/AboutSection.vue";
import BeforeAfterSection from "./components/BeforeAfterSection.vue";
import ServiceSection from "./components/ServiceSection.vue";
import TestimoniesSection from "./components/TestimoniesSection.vue";
import FooterSection from "./components/FooterSection.vue";
</script>
