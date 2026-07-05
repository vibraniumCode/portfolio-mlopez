<script lang="ts" setup>
import { ref } from "vue";

/*
ref es una función de Vue que crea una variable reactiva — cuando su valor cambia, 
Vue automáticamente actualiza lo que se muestra en pantalla. 
Es diferente a una variable normal de JavaScript: si hacés let x = false y cambiás x = true, Vue no se entera. Con ref, sí.
*/
const menuAbierto = ref(false);

const toggleMenu = () => {
  menuAbierto.value = !menuAbierto.value;
};
</script>

<template>
  <!-- fixed top-0 left-0 w-full → el nav queda pegado arriba mientras scrolleás -->
  <!-- z-50 → para que quede por encima de todo -->
  <!-- h-16 → altura fija de 64px (16 por 4px, la escala de Tailwind) -->
  <!-- flex items-center justify-between → los 3 elementos (logo, links, botón) se distribuyen horizontalmente con espacio entre ellos -->
  <nav
    class="fixed top-0 left-0 w-full z-50 bg-white border-b border-gray-200 px-8 h-16 flex items-center justify-between"
  >
    <div class="text-xl font-bold text-black">
      Mlopez<span class="text-lime-500">.</span>
    </div>
    <!-- Links — ocultos en mobile, visibles en desktop -->
    <ul class="hidden md:flex gap-8 list-none">
      <li>
        <a
          href="#inicio"
          class="text-sm text-gray-500 hover:text-black transition-colors"
          >Inicio</a
        >
      </li>
      <li>
        <a
          href="#tech-stack"
          class="text-sm text-gray-500 hover:text-black transition-colors"
          >Tecnologías</a
        >
      </li>
      <li>
        <a
          href="#contact"
          class="text-sm text-gray-500 hover:text-black transition-colors"
          >Contacto</a
        >
      </li>
    </ul>
    <!-- Botón CTA — oculto en mobile -->
    <a
      href="#contact"
      class="hidden md:block bg-black text-white text-sm px-5 py-2 hover:bg-lime-500 hover:text-black transition-colors"
      >Hablemos →</a
    >
    <!-- Botón hamburguesa — visible solo en mobile -->
    <!--@click="toggleMenu" → cuando clickeás, llama a la función toggleMenu que cambia menuAbierto de true a false o viceversa.
     menuAbierto ? '✕' : '☰'  → si el menú está abierto muestra ✕, si está cerrado muestra ☰. Esto se llama expresión ternaria — es JavaScript dentro del template.-->
    <button class="md:hidden text-2xl text-black" @click="toggleMenu">
      {{ menuAbierto ? "X" : "☰" }}
    </button>
  </nav>

  <!-- Menu mobile desplegable -->
  <!--v-show="menuAbierto" → muestra el menú desplegable solo cuando menuAbierto es true-->
  <div v-show="menuAbierto" class="fixed top-16 left-0 w-full bg-white border-b
  border-gray-200 z-40 flex flex-col px-8 py-6 gap-6 md:hidden">
    <a href="#inicio" class="text-sm text-gray-700 hover:text-black transition-colors" @click="toggleMenu">Inicio</a>
    <a href="#tech-stack" class="text-sm text-gray-700 hover:text-black transition-colors" @click="toggleMenu">Tecnología</a>
    <a href="#contact" class="text-sm text-gray-700 hover:text-black transition-colors" @click="toggleMenu">Contacto</a>
    <a href="#contact" class="bg-black text-white text-sm px-5 py-3 text-center hover:bg-lime-500 hover:text-black transition-colors" @click="toggleMenu">Hablemos →</a>
  </div>
</template>
