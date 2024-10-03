<template>
  <div class="min-h-screen font-serif flex items-center justify-center bg-gray-100 relative overflow-hidden">
    <div
        v-for="(circle, index) in circles"
        :key="index"
        class="absolute rounded-full"
        :style="{
        width: circle.size + 'px',
        height: circle.size + 'px',
        top: circle.y + 'px',
        left: circle.x + 'px',
        backgroundColor: circle.color,
        transform: 'translate(-50%, -50%)',
        transition: 'transform 0.5s ease',
      }"
    ></div>
    <div class="text-center p-6 z-10">
      <h1 class="text-4xl md:text-6xl font-bold font-serif">
        Coming Soon
      </h1>
      <p class="text-lg md:text-xl text-gray-700 mb-8">
        We are working hard to bring something amazing. Stay tuned!
      </p>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const circles = ref([]);

const createCircle = (event) => {
  const newCircle = {
    x: event.clientX,
    y: event.clientY,
    size: Math.random() * 50 + 20, // Random size between 20 and 70
    color: `hsl(${Math.random() * 360}, 100%, 75%)`, // Random pastel color
  };
  circles.value.push(newCircle);
};

onMounted(() => {
  window.addEventListener('mousemove', createCircle);
});
</script>

<style scoped>
body {
  font-family: 'Jost', sans-serif;
}
</style>
