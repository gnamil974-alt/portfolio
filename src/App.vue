<script setup>
import AppHeader from './components/layout/AppHeader.vue'
import AppFooter from './components/layout/AppFooter.vue'
import HeroSection from './components/sections/HeroSection.vue'
import AboutSection from './components/sections/AboutSection.vue'
import WorkSection from './components/sections/WorkSection.vue'
import PortfolioSection from './components/sections/PortfolioSection.vue'
import ContactSection from './components/sections/ContactSection.vue'
</script>

<template>
  <AppHeader />
  <main>
    <HeroSection />
    <AboutSection />
    <WorkSection />
    <PortfolioSection />
    <ContactSection />
  </main>
  <AppFooter />
</template>
