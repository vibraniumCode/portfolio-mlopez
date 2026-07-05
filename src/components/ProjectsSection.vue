<script setup lang="ts">
import imgBarberia from "@/assets/proyecto-barberia.png";
import imgVibranium from "@/assets/proyecto-vibranium.png";
import imgAmelie from "@/assets/proyecto-amelie.png";

const proyectos = [
  {
    id: 1,
    tipo: "Proyecto propio",
    nombre: "Iron Blade — Barbería App",
    descripcion:
      "Sistema completo de gestión para barberías. Desde la reserva de turnos hasta el control total del negocio, con dashboards en tiempo real y múltiples roles de usuario.",
    imagen: imgBarberia,
    features: [
      "Reserva de turnos online",
      "Dashboard con gráficos de ingresos",
      "Gestión de barberos y servicios",
      "Vista de agenda en tiempo real",
      "Listado y gestión de clientes",
      "4 roles: Cliente, Barbero, Admin, SuperAdmin",
    ],
    stack: ["Vue", "TypeScript", "Node.js", "MongoDB", "Socket.io"],
    link: "https://barber-frontend-gray.vercel.app",
    badge: "bg-lime-500 text-black",
    publica: true,
  },
  {
    id: 2,
    tipo: "Proyecto propio",
    nombre: "VibraniumCode — Estudio de Software",
    descripcion:
      "Landing page profesional de mi estudio de desarrollo. Presenta servicios, proyectos, stack tecnológico y formulario de contacto. Diseño oscuro y moderno orientado a conversión.",
    imagen: imgVibranium,
    features: [
      "Diseño dark mode profesional",
      "Secciones de servicios y proyectos",
      "Stack tecnológico completo",
      "Formulario de contacto funcional",
      "Totalmente responsive",
      "Deploy en Vercel",
    ],
    stack: ["Vue", "TypeScript", "Tailwind", "Vite"],
    link: "https://vibraniumcode.com",
    badge: "bg-lime-500 text-black",
    publica: true,
  },
  {
    id: 3,
    tipo: "Proyecto propio",
    nombre: "By Amelie — Tienda Online",
    descripcion:
      "E-commerce completo de productos para el hogar. Catálogo con más de 200 productos, carrito, wishlist, panel admin con dashboard de ventas en tiempo real, gestión de pedidos y notificaciones para email.",
    imagen: imgAmelie,
    features: [
      "Catálogo con filtros por categoría",
      "Carrito de compras",
      "Panel de administración",
      "Dashboard de ventas en tiempo real",
      "Gestión de pedidos y stock",
      "Notificaciones por email",
    ],
    stack: ["Vue", "TypeScript", "Tailwind", "Node.js", "MongoDB"],
    link: "https://by-amelie.vercel.app",
    badge: "bg-lime-500 text-black",
    publica: true,
  },
  {
    id: 4,
    tipo: "Experiencia profesional",
    nombre: "Integración SSN — CNP Seguros",
    descripcion:
      "Desarrollo de integración con la API de la Superintendencia de Seguros de la Nación (SSN). Solución end-to-end para el envío de datos regulatorios desde los sistemas internos de la aseguradora.",
    imagen: null,
    features: [
      "Stored Procedures para armado de JSON",
      "Pipeline completo con Talend",
      "Autenticación automática con la API SSN",
      "Control y trazabilidad de envíos",
      "Manejo de errores y reintentos",
      "Tablas de auditoría y logging",
    ],
    stack: ["SQL Server", "Talend"],
    link: null,
    badge: "bg-blue-600 text-white",
    publica: false,
  },
];
</script>

<template>
  <section id="proyectos" class="py-24 bg-white px-8">
    <div class="max-w-6xl mx-auto">
      <div class="mb-16 text-center md:text-left">
        <p class="text-xs text-gray-400 uppercase tracking-widest mb-2">
          Mi trabajo
        </p>
        <h2 class="text-4xl md:text-5xl font-black text-black uppercase">
          Proyectos <span class="text-lime-500">&</span> Experiencia
        </h2>
      </div>

      <div class="flex flex-col gap-16">
        <div
          v-for="(proyecto, index) in proyectos"
          :key="proyecto.id"
          class="grid grid-cols-1 md:grid-cols-2 gap-10 items-center"
          :class="index % 2 !== 0 ? 'md:grid-flow-dense' : ''"
        >
          <!-- Imagen o placeholder -->
          <div
            class="rounded-2xl overflow-hidden aspect-video bg-gray-100 flex items-center justify-center"
            :class="index % 2 !== 0 ? 'md:col-start-2' : ''"
          >
            <img
              v-if="proyecto.imagen"
              :src="proyecto.imagen"
              :alt="proyecto.nombre"
              class="w-full h-full object-cover object-top hover:object-bottom transition-all duration-[3s]"
            />
            <div
              v-else
              class="flex flex-col items-center gap-3 p-8 text-center"
            >
              <span class="text-5xl">🏢</span>
              <p class="text-sm text-gray-400 font-medium">
                Proyecto confidencial
              </p>
              <p class="text-xs text-gray-400">
                CNP Seguros — Información reservada
              </p>
            </div>
          </div>

          <!-- Info -->
          <div
            class="flex flex-col gap-5"
            :class="index % 2 !== 0 ? 'md:col-start-1 md:row-start-1' : ''"
          >
            <div class="flex items-center gap-3">
              <span
                class="text-xs font-bold px-3 py-1 rounded-full"
                :class="proyecto.badge"
              >
                {{ proyecto.tipo }}
              </span>
              <span
                v-if="!proyecto.publica"
                class="text-xs text-gray-400 flex items-center gap-1"
              >
                🔒 Confidencial
              </span>
            </div>

            <h3
              class="text-2xl md:text-3xl font-black text-black uppercase leading-tight"
            >
              {{ proyecto.nombre }}
            </h3>

            <p class="text-gray-600 text-sm leading-relaxed">
              {{ proyecto.descripcion }}
            </p>

            <ul class="grid grid-cols-1 sm:grid-cols-2 gap-2">
              <li
                v-for="feature in proyecto.features"
                :key="feature"
                class="flex items-start gap-2 text-sm text-gray-600"
              >
                <span class="text-lime-500 mt-0.5 flex-shrink-0">✓</span>
                {{ feature }}
              </li>
            </ul>

            <div class="flex flex-wrap gap-2">
              <span
                v-for="tech in proyecto.stack"
                :key="tech"
                class="text-xs bg-gray-100 text-gray-600 px-3 py-1 rounded-full"
              >
                {{ tech }}
              </span>
            </div>

            <a
              v-if="proyecto.link"
              :href="proyecto.link"
              target="_blank"
              class="self-start bg-black text-white px-6 py-3 text-sm font-medium hover:bg-lime-500 hover:text-black transition-colors flex items-center gap-2"
            >
              Ver proyecto →
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
<!--index % 2 !== 0 → los proyectos pares tienen imagen a la izquierda, los impares a la derecha. 
Así cada card se ve distinta sin escribir código diferente para cada una.
object-top hover:object-bottom la captura de barbería es larga — al hacer hover scrollea suavemente 
de arriba a abajo mostrando toda la app. Eso es todo CSS, sin JavaScript.
transition-all duration-[3s] la transición dura 3 segundos para que el scroll de la imagen sea suave y se 
vea toda la app.
v-if="proyecto.imagen"  si no hay imagen (CNP) muestra el placeholder con 🔒.-->
