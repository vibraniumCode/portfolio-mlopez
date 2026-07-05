<script setup lang="ts">
const tecnologias = [
  {
    nombre: "Vue",
    logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vuejs/vuejs-original.svg",
  },
  {
    nombre: "TypeScript",
    logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg",
  },
  {
    nombre: "Tailwind",
    logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/tailwindcss/tailwindcss-original.svg",
  },
  {
    nombre: "Node.js",
    logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg",
  },
  {
    nombre: "SQL Server",
    logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/microsoftsqlserver/microsoftsqlserver-original.svg",
  },
  {
    nombre: "Angular",
    logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/angular/angular-original.svg",
  },
  {
    nombre: "C#",
    logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg",
  },
  {
    nombre: ".NET",
    logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/dotnetcore/dotnetcore-original.svg",
  },
  {
    nombre: "Azure DevOps",
    logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/azuredevops/azuredevops-original.svg",
  },
  {
    nombre: "MongoDB",
    logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mongodb/mongodb-original.svg",
  },
  {
    nombre: "Git",
    logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg",
  },
  {
    nombre: "Postman",
    logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/postman/postman-original.svg",
  },
];
</script>

<template>
  <section id="tech-stack" class="py-24 bg-gray-50 px-8 overflow-hidden">
    <div class="max-w-6xl mx-auto mb-12 text-center md:text-left">
      <p class="text-xs text-gray-400 uppercase tracking-widest mb-2">
        Herramientas
      </p>
      <h2 class="text-4xl md:text-5xl font-black text-black uppercase">
        Tech <span class="text-lime-500">Stack</span>
      </h2>
    </div>

    <!-- Carousel wrapper -->
    <div class="relative overflow-hidden">
      <div class="flex gap-8 carousel-track">
        <!-- Primera pasada -->
        <div
          v-for="tech in tecnologias"
          :key="tech.nombre"
          class="flex-shrink-0 bg-white border border-gray-200 rounded-xl p-5 flex flex-col items-center gap-3 w-32 hover:border-lime-500 hover:shadow-md transition-all"
        >
          <img
            :src="tech.logo"
            :alt="tech.nombre"
            class="w-10 h-10 object-contain"
          />
          <span class="text-xs font-medium text-gray-700 text-center">{{
            tech.nombre
          }}</span>
        </div>

        <!-- Segunda pasada (duplicado para loop infinito) -->
        <div
          v-for="tech in tecnologias"
          :key="tech.nombre + '-dup'"
          class="flex-shrink-0 bg-white border border-gray-200 rounded-xl p-5 flex flex-col items-center gap-3 w-32 hover:border-lime-500 hover:shadow-md transition-all"
          aria-hidden="true"
        >
          <img
            :src="tech.logo"
            :alt="tech.nombre"
            class="w-10 h-10 object-contain"
          />
          <span class="text-xs font-medium text-gray-700 text-center">{{
            tech.nombre
          }}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.carousel-track {
  animation: scroll 25s linear infinite;
  width: max-content;
}

.carousel-track:hover {
  animation-play-state: paused;
}

@keyframes scroll {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(-50%);
  }
}
</style>
<!--animation-play-state: paused → cuando el usuario pasa el mouse, 
el carousel se pausa. Es un detalle de UX muy simple pero muy efectivo.-->
