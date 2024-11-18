<template>
  <div>
    <NavBar />
    <SearchBar @search="handleSearch" />
    <HouseList :houses="filteredHouses" />
    
  </div>
</template>

<script>
import axios from 'axios';
import HouseList from '~/components/HouseList.vue';
import SearchBar from '~/components/SearchBar.vue';
import Navbar from '@/components/NavBar.vue';

export default {
  components: {
    HouseList,
    SearchBar,
    NavBar,
  },
  data() {
    return {
      houses: [],
      filteredHouses: [],
    };
  },
  async fetch() {
    try {
      const response = await axios.get('/houses/houses.json');
      this.houses = response.data;
      this.filteredHouses = response.data;
    } catch (error) {
      console.error('Error loading houses:', error);
    }
  },
  methods: {
    handleSearch(query) {
      // Filtrar los personajes según el término de búsqueda
      this.filteredHouses = this.houses.filter((house) =>
        house.House_name.toLowerCase().includes(query.toLowerCase())
      );
    },
  },
};
</script>

<style scoped>
/* Agrega estilos para la página de las casas aquí */
</style>