<script setup lang="ts">
const experiencias = [
  {
    id: 1,
    empresa: "VibraniumCode",
    rol: "Desarrollador Freelance — Fundador",
    periodo: "Ene 2025 — Presente",
    tipo: "Emprendimiento propio",
    badge: "bg-lime-500 text-black",
    items: [
      "Desarrollo de aplicaciones web y soluciones de software a medida",
      "Gestión integral del ciclo de desarrollo: relevamiento, arquitectura, desarrollo, despliegue y soporte",
      "Sistemas de gestión, herramientas internas y plataformas web",
      "Stack: Vue.js, TypeScript, Python, SQL/NoSQL",
    ],
  },
  {
    id: 2,
    empresa: "CNP Seguros",
    rol: "Analista IT — Soporte, Desarrollo y Optimización",
    periodo: "Sep 2024 — Presente",
    tipo: "Relación de dependencia",
    badge: "bg-blue-600 text-white",
    items: [
      "Diseño y optimización de bases de datos SQL: stored procedures, funciones y estructuras escalables",
      "Automatización de procesos con Talend Open Studio y SQL Server",
      "Desarrollo y mantenimiento de aplicaciones web en Angular, TypeScript, Tailwind, .NET y SQL Server",
      "Integración con API SSN: generación y envío de información regulatoria de cartera",
    ],
  },
  {
    id: 3,
    empresa: "CNP Seguros",
    rol: "Analista de Soporte de Aplicaciones — BAU",
    periodo: "Ene 2022 — Sep 2024",
    tipo: "Relación de dependencia",
    badge: "bg-blue-400 text-white",
    items: [
      "Soporte y mantenimiento de sistemas centrales",
      "Desarrollo y optimización de consultas en SQL Server",
      "Reportes con SQL Server Reporting Services (SSRS)",
      "Automatización de procesos con Talend Open Studio",
      "Gestión de incidentes en entornos productivos bajo metodología Scrum",
    ],
  },
  {
    id: 4,
    empresa: "SISTRAN Consultores",
    rol: "Programador Visual Basic",
    periodo: "Sep 2019 — Dic 2021",
    tipo: "Relación de dependencia",
    badge: "bg-gray-500 text-white",
    items: [
      "Desarrollo y mantenimiento de aplicaciones en Visual Basic 6.0 para el negocio asegurador",
      "Gestión y optimización de bases de datos SQL Server",
      "Reportes dinámicos con Crystal Reports",
      "Participación en proyectos de migración hacia .NET",
      "Gestión de tareas con Jira bajo metodología Scrum",
    ],
  },
];
</script>

<template>
  <section id="experiencia" class="py-24 bg-gray-50 px-8">
    <div class="max-w-6xl mx-auto">
      <div class="mb-16 text-center md:text-left">
        <p class="text-xs text-gray-400 uppercase tracking-widest mb-2">
          Trayectoria
        </p>
        <h2 class="text-4xl md:text-5xl font-black text-black uppercase">
          Experiencia <span class="text-lime-500">Laboral</span>
        </h2>
      </div>

      <!-- Timeline -->
      <div class="relative">
        <!-- Línea vertical (solo desktop) -->
        <div
          class="hidden md:block absolute left-1/2 top-0 bottom-0 w-px bg-gray-200 -translate-x-1/2"
        ></div>

        <div class="flex flex-col gap-12">
          <div
            v-for="(exp, index) in experiencias"
            :key="exp.id"
            class="relative grid grid-cols-1 md:grid-cols-2 gap-6 md:gap-16 items-start"
          >
            <!-- Punto en la línea (solo desktop) -->
            <div
              class="hidden md:block absolute left-1/2 top-6 w-3 h-3 rounded-full bg-lime-500 -translate-x-1/2 ring-4 ring-white z-10"
            ></div>

            <!-- Card — alterna izquierda/derecha -->
            <div
              class="bg-white border border-gray-200 rounded-2xl p-6 flex flex-col gap-4 hover:border-lime-500 hover:shadow-md transition-all"
              :class="index % 2 === 0 ? 'md:col-start-1' : 'md:col-start-2'"
            >
              <div class="flex items-start justify-between gap-3 flex-wrap">
                <div>
                  <span
                    class="text-xs font-bold px-3 py-1 rounded-full"
                    :class="exp.badge"
                  >
                    {{ exp.tipo }}
                  </span>
                  <h3 class="text-lg font-black text-black uppercase mt-2">
                    {{ exp.empresa }}
                  </h3>
                  <p class="text-sm font-medium text-gray-600">{{ exp.rol }}</p>
                </div>
                <span class="text-xs text-gray-400 whitespace-nowrap">{{
                  exp.periodo
                }}</span>
              </div>

              <ul class="flex flex-col gap-2">
                <li
                  v-for="item in exp.items"
                  :key="item"
                  class="flex items-start gap-2 text-sm text-gray-600"
                >
                  <span class="text-lime-500 mt-0.5 flex-shrink-0">✓</span>
                  {{ item }}
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
