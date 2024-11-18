<template>
    <div>
      <Navbar />
      <SearchBar @search="handleSearch" />
      <BattleList :battles="filteredBattles" />
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  import BattleList from '~/components/BattleList.vue';
  import SearchBar from '~/components/SearchBar.vue';
  import Navbar from '@/components/Navbar.vue';


  export default {
    components: {
      BattleList,
      SearchBar,
      Navbar,
    },
    data() {
      return {
        battles: [],
        filteredBattles: [],
      };
    },
    async fetch() {
      try {
        // Cargar el archivo JSON desde /static/data/battles.json
        const response = await axios.get('/battles/battles.json');
        this.battles = response.data.map((battle, index) => ({
          ...battle,
          battleLink: `/battles/${battle.name.replace(/\s+/g, '-')}`, // Agregar un enlace dinámico a cada batalla
        }));
        this.filteredBattles = this.battles;
      } catch (error) {
        console.error('Error loading battles:', error);
      }
    },
    methods: {
      handleSearch(query) {
        // Filtrar los personajes según el término de búsqueda
        this.filteredBattles = this.battles.filter((battle) =>
        battle.name.toLowerCase().includes(query.toLowerCase())
        );
      },
    },

  };
  </script>
  
  <style scoped>
  /* Puedes agregar estilos para la página de batallas aquí */
  </style>
  