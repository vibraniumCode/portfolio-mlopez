<template>
  <section class="py-24 bg-black px-8">
    <div class="max-w-6xl mx-auto grid grid-cols-2 md:grid-cols-4 gap-8">
      <div
        v-for="stat in stats"
        :key="stat.label"
        class="flex flex-col items-center text-center gap-2"
      >
        <span class="text-5xl md:text-6xl font-black text-white leading-none">
          {{ stat.numero }}<span class="text-lime-500">{{ stat.sufijo }}</span>
        </span>
        <span class="text-xs text-gray-400 uppercase tracking-widest">{{
          stat.label
        }}</span>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
const stats = [
  { numero: "6", sufijo: "", label: "Años de experiencia" },
  { numero: "6", sufijo: "+", label: "Proyectos desarrollados" },
  { numero: "4", sufijo: "", label: "Clientes en VibraniumCode" },
  { numero: "12", sufijo: "+", label: "Tecnologías en el stack" },
];
</script>
