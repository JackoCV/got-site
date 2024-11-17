<template>
    <div v-if="battle">
      <h1>{{ battle.name }}</h1>
      <p><strong>Year:</strong> {{ battle.year }}</p>
      <p><strong>Location:</strong> {{ battle.location }}</p>
      <p><strong>Region:</strong> {{ battle.region }}</p>
      <p><strong>Attacker King:</strong> {{ battle.attacker_king }}</p>
      <p><strong>Defender King:</strong> {{ battle.defender_king }}</p>
      <p><strong>Battle Type:</strong> {{ battle.battle_type }}</p>
      <!-- Agrega más detalles según lo que haya en el archivo JSON -->
    </div>
    <div v-else>
      <p>Loading battle details...</p>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        battle: null,
      };
    },
    async fetch() {
      try {
        // Obtener el `battle_number` desde la ruta
        const battleNumber = this.$route.params.id;
        // Cargar los datos de batallas
        const response = await axios.get('/battles/battles.json');
        // Buscar la batalla por `battle_number`
        this.battle = response.data.find((b) => b.battle_number == battleNumber);
      } catch (error) {
        console.error('Error loading battle:', error);
      }
    },
  };
  </script>
  
  <style scoped>
  /* Agrega estilos para la página de detalles */
  </style>
  