<template>
  <div>
    <NavBar />
    <SearchBar @search="handleSearch" />
    <CharacterList :characters="filteredCharacters" />
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from '~/components/SearchBar.vue';
import CharacterList from '~/components/CharacterList.vue';
import NavBar from '~/components/NavBar.vue';

export default {
  components: {
    SearchBar,
    CharacterList,
    NavBar
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
  }
  ,
  methods: {
    handleSearch(query) {
      // Filtrar los personajes según el término de búsqueda
      this.filteredCharacters = this.characters.filter((character) =>
        character.name.toLowerCase().includes(query.toLowerCase())
      );
    },
  },
};
</script>

<style scoped>
/* Agrega estilos para tu página aquí */
</style>