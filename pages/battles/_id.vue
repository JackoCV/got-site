<template>
  <div v-if="battle">
    <h1>{{ battle.name }}</h1>
    <p><strong>Year:</strong> {{ battle.year }}</p>
    <p><strong>Battle Number:</strong> {{ battle.battle_number }}</p>
    <p><strong>Attacker King:</strong> {{ battle.attacker_king }}</p>
    <p><strong>Defender King:</strong> {{ battle.defender_king }}</p>
    <p><strong>Region:</strong> {{ battle.region }}</p>
    <p><strong>Location:</strong> {{ battle.location }}</p>
    <!-- Agrega más detalles de la batalla aquí -->
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
      // Obtener el battleLink de la batalla desde la ruta
      const link = this.$route.params.id; // Usando el "id" de la URL para buscar la batalla
      // Cargar los datos de las batallas
      const response = await axios.get('/battles/battles.json');
      // Buscar la batalla por battleLink
      this.battle = response.data.find((b) => b.battleLink === `/battles/${link}`);
    } catch (error) {
      console.error('Error loading battle:', error);
    }
  },
};
</script>

<style scoped>
/* Agrega estilos para la página de detalles de batallas aquí */
</style>
