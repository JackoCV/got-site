<template>
    <div>
      <h1>Game of Thrones Battles</h1>
      <BattleList :battles="battles" />
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  import BattleList from '~/components/BattleList.vue';
  
  export default {
    components: {
      BattleList,
    },
    data() {
      return {
        battles: [],
      };
    },
    async fetch() {
      try {
        // Cargar el archivo JSON desde /static/data/battles.json
        const response = await axios.get('/battles/battles.json');
        this.battles = response.data.map((battle, index) => ({
          ...battle,
          battleLink: `/battles/${index}`, // Agregar un enlace dinámico a cada batalla
        }));
      } catch (error) {
        console.error('Error loading battles:', error);
      }
    },
  };
  </script>
  
  <style scoped>
  /* Puedes agregar estilos para la página de batallas aquí */
  </style>
  