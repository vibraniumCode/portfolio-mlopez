<script setup lang="ts">
import { ref } from "vue";
import emailjs from "@emailjs/browser";

const nombre = ref("");
const email = ref("");
const motivo = ref("");
const mensaje = ref("");
const enviado = ref(false);
const error = ref(false);
const cargando = ref(false);

const enviar = async () => {
  if (!nombre.value || !email.value || !mensaje.value) return;

  cargando.value = true;
  error.value = false;

  try {
    await emailjs.send(
      "service_rc9vpib", // reemplazá con tu Service ID
      "template_7ayacrm", // reemplazá con tu Template ID
      {
        nombre: nombre.value,
        email: email.value,
        motivo: motivo.value,
        mensaje: mensaje.value,
      },
      "KXU9Q63D7u0V1qxqI", // reemplazá con tu Public Key
    );

    enviado.value = true;
    nombre.value = "";
    email.value = "";
    motivo.value = "";
    mensaje.value = "";

    setTimeout(() => {
      enviado.value = false;
    }, 4000);
  } catch (e) {
    error.value = true;
    setTimeout(() => {
      error.value = false;
    }, 4000);
  } finally {
    cargando.value = false;
  }
};
</script>

<template>
  <section id="contact" class="py-24 bg-white px-8">
    <div
      class="max-w-6xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-16 items-start"
    >
      <!-- Info izquierda -->
      <div class="flex flex-col gap-8">
        <div>
          <p class="text-xs text-gray-400 uppercase tracking-widest mb-2">
            Contacto
          </p>
          <h2
            class="text-4xl md:text-5xl font-black text-black uppercase leading-tight"
          >
            ¿Tenés un proyecto,<br />
            querés <span class="text-lime-500">contratarme</span><br />
            o sumarme a<br />tu equipo?
          </h2>
        </div>

        <p class="text-gray-600 text-sm leading-relaxed">
          Estoy disponible para proyectos freelance, oportunidades laborales o
          colaboraciones. Respondó dentro de las 24 horas.
        </p>

        <div class="flex flex-col gap-4">
          <a
            href="mailto:vibraniumcode@gmail.com"
            class="flex items-center gap-3 group"
          >
            <div
              class="w-10 h-10 bg-gray-100 rounded-full flex items-center justify-center group-hover:bg-lime-500 transition-colors"
            >
              <span class="text-sm">✉</span>
            </div>
            <span
              class="text-sm text-gray-600 group-hover:text-black transition-colors"
              >vibraniumcode@gmail.com</span
            >
          </a>

          <a
            href="https://wa.me/541154251100"
            target="_blank"
            class="flex items-center gap-3 group"
          >
            <div
              class="w-10 h-10 bg-gray-100 rounded-full flex items-center justify-center group-hover:bg-lime-500 transition-colors"
            >
              <span class="text-sm">📱</span>
            </div>
            <span
              class="text-sm text-gray-600 group-hover:text-black transition-colors"
              >+54 11 5425-1100</span
            >
          </a>

          <a
            href="https://www.linkedin.com/in/marcos-antonio-lopez-561a69221/"
            target="_blank"
            class="flex items-center gap-3 group"
          >
            <div
              class="w-10 h-10 bg-gray-100 rounded-full flex items-center justify-center group-hover:bg-lime-500 transition-colors"
            >
              <span class="text-sm">💼</span>
            </div>
            <span
              class="text-sm text-gray-600 group-hover:text-black transition-colors"
              >LinkedIn — Marcos Lopez</span
            >
          </a>

          <a
            href="https://vibraniumcode.com"
            target="_blank"
            class="flex items-center gap-3 group"
          >
            <div
              class="w-10 h-10 bg-gray-100 rounded-full flex items-center justify-center group-hover:bg-lime-500 transition-colors"
            >
              <span class="text-sm">🌐</span>
            </div>
            <span
              class="text-sm text-gray-600 group-hover:text-black transition-colors"
              >vibraniumcode.com</span
            >
          </a>
        </div>
      </div>

      <!-- Formulario derecha -->
      <div class="flex flex-col gap-4">
        <!-- Mensajes de estado -->
        <div
          v-if="enviado"
          class="bg-lime-500 text-black p-4 rounded-xl text-sm font-medium text-center"
        >
          ✓ Mensaje enviado. Te respondo pronto!
        </div>

        <div
          v-if="error"
          class="bg-red-100 text-red-600 p-4 rounded-xl text-sm font-medium text-center"
        >
          ✗ Hubo un error al enviar. Intentá de nuevo.
        </div>

        <div class="flex flex-col gap-2">
          <label class="text-xs text-gray-400 uppercase tracking-widest"
            >Nombre</label
          >
          <input
            v-model="nombre"
            type="text"
            placeholder="Tu nombre"
            class="border border-gray-200 rounded-xl px-4 py-3 text-sm outline-none focus:border-lime-500 transition-colors"
          />
        </div>

        <div class="flex flex-col gap-2">
          <label class="text-xs text-gray-400 uppercase tracking-widest"
            >Email</label
          >
          <input
            v-model="email"
            type="email"
            placeholder="tu@email.com"
            class="border border-gray-200 rounded-xl px-4 py-3 text-sm outline-none focus:border-lime-500 transition-colors"
          />
        </div>

        <div class="flex flex-col gap-2">
          <label class="text-xs text-gray-400 uppercase tracking-widest"
            >Motivo</label
          >
          <select
            class="border border-gray-200 rounded-xl px-4 py-3 text-sm outline-none focus:border-lime-500 transition-colors text-gray-600"
          >
            <option value="">Seleccioná una opción</option>
            <option value="proyecto">Tengo un proyecto</option>
            <option value="contratar">Quiero contratarte</option>
            <option value="equipo">Quiero sumarte a mi equipo</option>
            <option value="otro">Otro</option>
          </select>
        </div>

        <div class="flex flex-col gap-2">
          <label class="text-xs text-gray-400 uppercase tracking-widest"
            >Mensaje</label
          >
          <textarea
            v-model="mensaje"
            rows="5"
            placeholder="Contame más..."
            class="border border-gray-200 rounded-xl px-4 py-3 text-sm outline-none focus:border-lime-500 transition-colors resize-none"
          />
        </div>
        <!-- Botón -->
        <button
          @click="enviar"
          :disabled="cargando"
          class="bg-black text-white py-3 text-sm font-medium hover:bg-lime-500 hover:text-black transition-colors rounded-xl disabled:opacity-50 disabled:cursor-not-allowed"
        >
          {{ cargando ? "Enviando..." : "Enviar mensaje →" }}
        </button>
      </div>
    </div>
  </section>
</template>
