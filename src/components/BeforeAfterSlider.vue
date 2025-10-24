<template>
  <div
    ref="container"
    class="relative mx-auto w-full max-w-[900px] overflow-hidden rounded-3xl cursor-ew-resize select-none"
    :style="{ aspectRatio }"
    @mousedown="startDragging"
    @mouseup="stopDragging"
    @mouseleave="stopDragging"
    @mousemove="onDrag"
    @touchstart="startDragging"
    @touchend="stopDragging"
    @touchmove="onDrag"
  >
    <!-- AFTER Image (Full Width - Background Layer) -->
    <div class="absolute inset-0 w-full h-full">
      <img
        :src="after"
        alt="After"
        class="w-full h-full object-cover rounded-3xl"
      />
    </div>

    <!-- BEFORE Image Container (Clipped Layer) -->
    <div
      class="absolute inset-0 w-full h-full overflow-hidden"
      :style="{
        clipPath: `inset(0 ${100 - position}% 0 0)`,
        transition: isDragging ? 'none' : 'clip-path 0.3s ease-out',
      }"
    >
      <img
        :src="before"
        alt="Before"
        class="w-full h-full object-cover rounded-3xl"
      />
    </div>

    <!-- Divider Line -->
    <div
      class="absolute top-0 h-full w-[2px] bg-white z-[3]"
      :style="{
        left: position + '%',
        transition: isDragging ? 'none' : 'left 0.3s ease-out',
      }"
    ></div>

    <!-- Labels -->
    <div
      class="absolute top-4 left-4 bg-black/50 text-white px-3 py-1 rounded-full text-sm font-medium z-[4]"
    >
      Before
    </div>
    <div
      class="absolute top-4 right-4 bg-black/50 text-white px-3 py-1 rounded-full text-sm font-medium z-[4]"
    >
      After
    </div>

    <!-- Handle Button -->
    <div
      class="absolute top-1/2 w-12 h-12 rounded-full bg-white border-2 border-gray-300 flex items-center justify-center shadow-lg transform -translate-y-1/2 -translate-x-1/2 cursor-grab active:cursor-grabbing z-[5]"
      :style="{
        left: position + '%',
        transition: isDragging ? 'none' : 'left 0.3s ease-out',
      }"
    >
      <svg
        width="24"
        height="24"
        viewBox="0 0 24 24"
        fill="none"
        class="text-gray-600"
      >
        <path
          d="M8 7L4 12L8 17"
          stroke="currentColor"
          stroke-width="2"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
        <path
          d="M16 7L20 12L16 17"
          stroke="currentColor"
          stroke-width="2"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
      </svg>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from "vue";

const props = defineProps({
  before: String,
  after: String,
});

const position = ref(50);
const isDragging = ref(false);
const container = ref(null);
const aspectRatio = ref("4 / 3");

// Deteksi ukuran gambar dan set 50% ukuran asli
const loadImageAspectRatio = () => {
  const img = new Image();
  img.onload = () => {
    if (img.width && img.height) {
      aspectRatio.value = `${img.width} / ${img.height}`;
    }
  };
  img.src = props.after || props.before;
};

// Load aspect ratio saat component mounted atau gambar berubah
watch(() => [props.before, props.after], loadImageAspectRatio, {
  immediate: true,
});

const startDragging = () => (isDragging.value = true);
const stopDragging = () => (isDragging.value = false);

const onDrag = (e) => {
  if (!isDragging.value || !container.value) return;

  const rect = container.value.getBoundingClientRect();
  const clientX = e.touches ? e.touches[0].clientX : e.clientX;
  const newPos = ((clientX - rect.left) / rect.width) * 100;

  // Batasi slider antara 0% - 100%
  position.value = Math.min(Math.max(newPos, 0), 100);
};
</script>
