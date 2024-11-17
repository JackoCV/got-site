<template>
    <div>
      <HouseList :houses="filteredHouses" />
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  import HouseList from '~/components/HouseList.vue';
  
  export default {
    components: {
      HouseList,
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
  };
  </script>
  
  <style scoped>
  /* Agrega estilos para la página de las casas aquí */
  </style>
  