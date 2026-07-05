<script setup lang="ts">
import { Linkedin, Instagram, Github, Mail, Phone } from "lucide-vue-next";

const redes = [
  {
    icon: Linkedin,
    url: "https://www.linkedin.com/in/marcos-antonio-lopez-561a69221/",
  },
  { icon: Instagram, url: "https://www.instagram.com/vibraniumcode/" },
  { icon: Github, url: "https://github.com/vibraniumCode" },
  { icon: Mail, url: "mailto:vibraniumcode@gmail.com" },
  { icon: Phone, url: "https://wa.me/541154251100" },
];
</script>

<template>
  <section id="hero" class="min-h-screen pt-16 bg-white flex items-center px-8">
    <!--grid-cols-1 md:grid-cols-3 → en mobile es 1 columna (todo apilado), en desktop vuelve a 3 columnas-->
    <div
      class="max-w-6xl mx-auto w-full grid grid-cols-1 md:grid-cols-3 gap-8 items-center py-12"
    >
      <!-- COLUMNA IZQUIERDA 
      order-1/2/3 → en mobile la foto va primero (arriba), después el texto izquierdo, después la info derecha. 
      En desktop se ignora el order y vuelve al orden natural del grid
      -->
      <!--text-center md:text-left → centrado en mobile, alineado a la izquierda en desktop-->
      <!--items-center md:items-start → el botón y los elementos se centran en mobile-->
      <div
        class="flex flex-col gap-6 order-2 md:order-1 text-center md:text-left items-center md:items-start"
      >
        <p class="text-sm text-gray-400 tracking-widest uppercase">Hola, soy</p>
        <h1 class="text-5xl md:text-6xl font-black text-black leading-none">
          MARCOS<br />LOPEZ
        </h1>
        <p class="text-gray-600 text-sm leading-relaxed not-italic">
          Full Stack Developer con experiencia en Vue, TypeScript, .NET y SQL
          Server. Me especializo en proyectos grandes, liderando equipos y
          construyendo soluciones que conectan tecnología con las necesidades
          reales del negocio.
        </p>
        <a
          href="#contact"
          class="self-start bg-black text-white px-6 py-3 text-sm font-medium hover:bg-lime-500 hover:text-black transition-colors flex items-center gap-2"
        >
          Hablemos →
        </a>
      </div>

      <!-- COLUMNA CENTRO: foto + redes -->
      <!--max-w-xs mx-auto → en mobile la foto no ocupa todo el ancho, queda contenida y centrada-->
      <div
        class="relative bg-gray-100 rounded-2xl overflow-hidden flex items-center justify-center aspect-[3/4] order-1 md:order-2 max-w-xs mx-auto w-full md:max-w-none"
      >
        <!-- Foto 
        object-top le dice que cuando recorte la imagen, empiece desde arriba — así la cara queda siempre visible.
        -->
        <img
          src="@/assets/foto-marcos.png"
          alt="MLopez"
          class="w-full h-full object-cover object-top"
        />

        <!-- Badge disponible -->
        <div
          class="absolute bottom-4 left-1/2 -translate-x-1/2 bg-white px-4 py-2 rounded-full flex items-center gap-2 shadow-md whitespace-nowrap"
        >
          <!--animate-pulse → clase de Tailwind que hace que el punto verde parpadee solo, sin escribir ningún CSS.-->
          <span class="w-2 h-2 rounded-full bg-lime-500 animate-pulse"></span>
          <span class="text-xs font-medium text-gray-700"
            >Disponible para proyectos</span
          >
        </div>

        <!-- Redes sociales (barra derecha dentro del cuadro) -->
        <div
          class="absolute right-3 top-1/2 -translate-y-1/2 flex flex-col gap-3"
        >
          <!--v-for="red in redes" → itera el array redes del script y crea un 
          a> por cada red social. Así no repetís el mismo HTML 5 veces.-->
          <!--:key="red.url"→Vue necesita un identificador único por cada elemento del v-for
            para rastrear cambios eficientemente.-->
          <!--:href="red.url" → el : antes de href significa 
            que el valor es JavaScript (una variable), no texto literal.-->
          <!--component :is="red.icon" → renderiza dinámicamente el ícono correcto. 
            :is recibe el componente importado de Lucide.-->
          <a
            v-for="red in redes"
            :key="red.url"
            :href="red.url"
            target="_blank"
            class="w-9 h-9 bg-gray-500 rounded-full flex items-center justify-center shadow-md hover:bg-lime-500 transition-colors"
          >
            <component :is="red.icon" class="w-4 h-4 text-white" />
          </a>
        </div>
      </div>

      <!-- COLUMNA DERECHA -->
      <div
        class="flex flex-col gap-6 order-3 items-center md:items-start text-center md:text-left"
      >
        <div
          class="border border-gray-200 p-4 rounded-xl w-full flex flex-col gap-3"
        >
          <p class="text-xs text-gray-400 uppercase tracking-widest">
            Empresas
          </p>

          <div class="flex flex-col gap-1">
            <p class="text-sm font-semibold text-black">CNP Seguros</p>
            <p class="text-xs text-gray-400">Analista IT · 5 años</p>
          </div>

          <div class="w-full h-px bg-gray-100"></div>

          <div class="flex flex-col gap-1">
            <p class="text-sm font-semibold text-black">VibraniumCode</p>
            <p class="text-xs text-gray-400">Fundador & Dev Lead</p>
          </div>
        </div>

        <div>
          <p class="text-xs text-gray-400 uppercase tracking-widest mb-2">
            Especialidad
          </p>
          <h2
            class="text-2xl md:text-3xl font-black text-black leading-tight uppercase"
          >
            Full Stack<br />Developer
          </h2>
        </div>

        <div class="flex flex-col gap-2">
          <p class="text-xs text-gray-400 uppercase tracking-widest">
            Stack principal
          </p>
          <div class="flex flex-wrap gap-2 justify-center md:justify-start">
            <span
              v-for="tech in [
                'Vue',
                'TypeScript',
                '.NET',
                'SQL Server',
                'Node.js',
              ]"
              :key="tech"
              class="text-xs bg-gray-100 text-gray-600 px-3 py-1 rounded-full"
            >
              {{ tech }}
            </span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
