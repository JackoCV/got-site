<template>
    <div class="search-bar">
      <input type="text" v-model="query" placeholder="Search..." />
      <button @click="emitSearch">Search</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        query: '',
      };
    },
    methods: {
      emitSearch() {
        this.$emit('search', this.query);
      },
    },
  };
  </script>
  
  <style scoped>
  .search-bar {
    display: flex;
    gap: 0.5rem;
    padding: 1rem;
  }
  </style>
  