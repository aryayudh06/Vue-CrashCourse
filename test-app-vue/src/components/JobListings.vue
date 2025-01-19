<script setup>
import JobListing from './JobListing.vue';
import { RouterLink } from 'vue-router';
import { ref, defineProps, onMounted, reactive } from 'vue';
import DotLoader from 'vue-spinner/src/DotLoader.vue'
import axios from 'axios';

const state = reactive({
  jobs: [],
  isLoading: true
})

defineProps({
  limit: Number,
  showButton: {
    type: Boolean,
    default: false,
  }
});

onMounted(async () => {
  try{
    const response = await axios.get('/api/jobs');
    state.jobs = response.data;
  } catch (error){
    console.error(error);
  } finally {
    state.isLoading = false;
  }
});
</script>

<template>
  <section class="bg-blue-50 px-4 py-10">
    <div class="container-xl lg:container m-auto">
      <h2 class="text-3xl font-bold text-green-500 mb-6 text-center">
        Job Listings
      </h2>
      <!--SHOW LOADING SPINNER IF LOADING TRUE-->
      <div v-if="state.isLoading" class="text-center text-gray-500 py-6">
        <DotLoader />
      </div>

      <!--Show job listing when done loading-->
      <div v-else class="grid grid-cols-1 gap-6 md:grid-cols-3 text-grey">
        <JobListing v-for="job in state.jobs.slice(0, limit || state.jobs.length)" 
        :key="job.id" 
        :job="job"/>
          <!-- <pre>{{ job[0].title }}</pre> -->
          <!-- {{ job.title }} -->
      </div>
    </div>
  </section>
  <section v-if="showButton" class="m-auto max-w-lg my-10 px-6">
      <RouterLink
        to="/jobs"
        class="block bg-black text-white text-center py-4 px-6 rounded-xl hover:bg-gray-700"
        >View All Jobs
        </RouterLink>
    </section>
  <!-- Job Listings -->
</template>