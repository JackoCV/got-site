<template>
  <div>
    <Navbar />
    <SearchBar @search="handleSearch" />
    <EpisodeList :episodes="filteredepisodes" />
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from '~/components/SearchBar.vue';
import EpisodeList from '~/components/EpisodeList.vue';
import Navbar from '@/components/Navbar.vue';

export default {
  components: {
    SearchBar,
    EpisodeList,
    Navbar,
  },
  data() {
    return {
      episodes: [], // Todos los episodios
      filteredepisodes: [], // Episodios filtrados por búsqueda
    };
  },
  async fetch() {
    try {
      // Cargar el archivo JSON desde /static/data/episodes.json
      const response = await axios.get('/characters/episodes.json');
      this.episodes = response.data.map((episode, index) => ({
        ...episode,
        episodeLink: `/episodes/${episode.episodeTitle.replace(/\s+/g, '-')}`,
      }));
      this.filteredepisodes = this.episodes; // Inicialmente, mostramos todos
    } catch (error) {
      console.error('Error loading episodes:', error);
    }
  },
  methods: {
    handleSearch(query) {
      // Filtrar los episodios según el término de búsqueda
      this.filteredepisodes = this.episodes.filter((episode) => {
        const episodeTitle = episode.episodeTitle || ''; // Asegura que episodeTitle sea una cadena vacía si es undefined
        return episodeTitle.toLowerCase().includes(query.toLowerCase());
      });
    },
  },
};
</script>

<style scoped>
/* Agrega estilos para tu página aquí */
</style>
