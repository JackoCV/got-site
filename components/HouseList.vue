<template>
    <div class="house-list">
      <HouseCard
        v-for="house in houses"
        :key="house.houseLink"
        :house="house"
      />
    </div>
  </template>
  
  <script>
  import HouseCard from './HouseCard.vue';
  
  export default {
    props: {
      houses: {
        type: Array,
        required: true,
      },
    },
    components: {
      HouseCard,
    },
  };
  </script>
  
  <style scoped>
  .house-list {
    display: flex;
    flex-wrap: wrap;
    gap: 1.5rem;
    justify-content: center;
    margin-top: 2rem;
  }
  </style>
  