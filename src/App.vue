<script setup lang="ts">
import TheNavbar from "@/components/TheNavbar.vue";
import HeroSection from "@/components/HeroSection.vue";
import TechStack from "@/components/TechStack.vue";
import ProjectsSection from "@/components/ProjectsSection.vue";
import ExperienceSection from "@/components/ExperienceSection.vue";
import StatsSection from "@/components/StatsSection.vue";
import ContactSection from "@/components/ContactSection.vue";
import TheFooter from "@/components/TheFooter.vue";
</script>

<template>
  <TheNavbar />
  <main>
    <HeroSection />
    <TechStack />
    <ProjectsSection />
    <ExperienceSection />
    <StatsSection />
    <ContactSection />
  </main>
  <TheFooter />
</template>
