<template>
  <div>
    <Navbar />
    <SearchBar @search="handleSearch" />
    <HouseList :houses="filteredHouses" />
  </div>
</template>

<script>
import axios from 'axios';
import HouseList from '~/components/HouseList.vue';
import SearchBar from '~/components/SearchBar.vue';
import Navbar from '@/components/Navbar.vue';

export default {
  components: {
    HouseList,
    SearchBar,
    Navbar,
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
      console.log("Search query:", query); // Para verificar que se reciba el valor de búsqueda
      // Filtrar las casas según el término de búsqueda
      this.filteredHouses = this.houses.filter((house) => {
        const houseName = house.House_name || ''; // Asegura que houseName sea una cadena vacía si es undefined
        return houseName.toLowerCase().includes(query.toLowerCase());
      });
    },
  },
};
</script>

<style scoped>
/* Agrega estilos para la página de las casas aquí */
</style>
