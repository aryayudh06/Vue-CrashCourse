<script setup>
  import Navbar from './components/Navbar.vue';
  import { RouterView } from 'vue-router';
  // import Hero from './components/Hero.vue';
  // import HomeCard from './components/HomeCard.vue';
  // import JobListings from './components/JobListings.vue';
</script>

<template>
  <Navbar />
  <RouterView />
  <!-- <Hero title="Test Title" subtitle="Test that Vue"/>
  <HomeCard />
  <JobListings :limit="3" :showButton="true" /> -->
</template>