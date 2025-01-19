<script setup>
import Hero from '@/components/Hero.vue';
import HomeCard from '@/components/HomeCard.vue';
import JobListings from '@/components/JobListings.vue';
</script>

<template>
  <Hero title="Explore your Jobs!" subtitle="Discover more offer on your job preference"/>
  <HomeCard />
  <JobListings :limit="3" :showButton="true" />
</template>