<template>

  <div>
    <NavBar />
    <SearchBar @search="handleSearch" />
    <EpisodeList :episodes="filteredepisodes" />
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from '~/components/SearchBar.vue';
import EpisodeList from '~/components/EpisodeList.vue';
import Navbar from '@/components/NavBar.vue';

export default {
  components: {
    SearchBar,
    EpisodeList,
    NavBar
  },
  data() {
    return {
      episodes: [], // Todos los personajes
      filteredepisodes: [], // Personajes filtrados por búsqueda
    };
  },
  async fetch() {
    try {
      // Cargar el archivo JSON desde /static/data/episodes.json
      const response = await axios.get('/characters/episodes.json');
      //console.log(response)
      this.episodes = response.data.map((episode, index) => ({
        ...episode,
        episodeLink: `/episodes/${episode.episodeTitle.replace(/\s+/g, '-')}`
      }));
      this.filteredepisodes = this.episodes; // Inicialmente, mostramos todos
    } catch (error) {
      console.error('Error loading episodes:', error);
    }
  }
  ,
  methods: {
    handleSearch(query) {
      // Filtrar los personajes según el término de búsqueda
      this.filteredepisodes = this.episodes.filter((episode) =>
        episode.episodeTitle.toLowerCase().includes(query.toLowerCase())
      );
    },
  },
};
</script>

<style scoped>
/* Agrega estilos para tu página aquí */
</style>