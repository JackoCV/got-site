<template>
  <div>
    <Navbar />
    <SearchBar @search="handleSearch" />
    <CharacterList :characters="filteredCharacters" />
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from '~/components/SearchBar.vue';
import CharacterList from '~/components/CharacterList.vue';
import Navbar from '@/components/Navbar.vue';

export default {
  components: {
    SearchBar,
    CharacterList,
    Navbar
  },
  data() {
    return {
      characters: [], // Todos los personajes
      filteredCharacters: [], // Personajes filtrados por búsqueda
    };
  },
  async fetch() {
    try {
      // Cargar el archivo JSON desde /static/data/characters.json
      const response = await axios.get('/characters/characters.json');
      this.characters = response.data.map((character, index) => ({
        ...character,
        characterLink: `/characters/${character.characterName.replace(/\s+/g, '-')}`
      }));
      this.filteredCharacters = this.characters; // Inicialmente, mostramos todos
    } catch (error) {
      console.error('Error loading characters:', error);
    }
  },
  methods: {
    handleSearch(query) {
      console.log("Search query:", query); // Para verificar que se reciba el valor de búsqueda
      // Filtrar los personajes según el término de búsqueda
      this.filteredCharacters = this.characters.filter((character) => {
        const characterName = characterName  || ''; // Asegura que characterName sea una cadena vacía si es undefined
        return characterName.toLowerCase().includes(query.toLowerCase());
      });
    },
  },
};
</script>

<style scoped>
/* Agrega estilos para tu página aquí */
</style>
