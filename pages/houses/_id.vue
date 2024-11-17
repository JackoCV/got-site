<template>
    <div v-if="house">
      <h1>{{ house.House_name }}</h1>
      <p><strong>Region:</strong> {{ house.Region }}</p>
    </div>
    <div v-else>
      <p>Loading house details...</p>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        house: null,
      };
    },
    async fetch() {
      try {
        // Obtener el "id" de la casa desde la URL
        const houseId = this.$route.params.id;
        // Cargar los datos de las casas desde el JSON
        const response = await axios.get('/houses/houses.json');
        // Buscar la casa que coincida con el "id" de la URL
        this.house = response.data.find(
          (h) =>
            h.House_name.toLowerCase().replace(/\s+/g, '-') === houseId
        );
      } catch (error) {
        console.error('Error loading house:', error);
      }
    },
  };
  </script>
  
  <style scoped>
  /* Agrega estilos para la página de detalles de la casa */
  </style>
  