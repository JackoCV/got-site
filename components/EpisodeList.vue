<template>
    <div class="container mt-4">
      <div class="row g-4">
        <div class="col-md-4 col-sm-6" v-for="episode in episodes" :key="episode.episodeLink">
          <EpisodeCard :episode="episode" />
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import EpisodeCard from './EpisodeCard.vue';
  
  export default {
    props: {
      episodes: {
        type: Array,
        required: true,
      },
    },
    components: {
      EpisodeCard,
    },
  };
  </script>
  
  <style scoped>
  /* Personalización adicional si es necesario */
  </style>
  