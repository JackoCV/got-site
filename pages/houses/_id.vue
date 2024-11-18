<template>
  <div>
    <NavBar />
   
    <div v-if="house">
      <h1>{{ house.House_name }}</h1>
      <p><strong>Region:</strong> {{ house.Region }}</p>
      <CharacterList :characters="characters" />
    </div>
    <div v-else>
      <p>Loading house details...</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import CharacterList from '~/components/CharacterList.vue';
import Navbar from '@/components/Navbar.vue';

export default {
  components: {
    CharacterList,
    NavBar,
  },
  data() {
    return {
      house: null,
      characters: [],
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
      const charactersResponse = await axios.get('/characters/characters.json');


      this.characters = charactersResponse.data.filter((c) => {
        if (typeof c.houseName === 'string') {
          // Si houseName es un string, procesarlo normalmente
          if (this.house.Region === '') {
            return c.houseName === this.house.Region;
          }
          return c.houseName === this.house.Region;
        } else if (Array.isArray(c.houseName)) {
          // Si houseName es un array, verificar si algún elemento coincide
          return c.houseName.some(
            (name) => name === this.house.Region
          );
        }
        // Si no es ni string ni array, descartarlo
        return false;
      });
    } catch (error) {
      console.error('Error loading house:', error);
    }
  },
};
</script>

<style scoped>
/* Agrega estilos para la página de detalles de la casa */
</style>