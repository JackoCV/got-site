<template>
  <div class="container mt-4">
    <div class="row g-4">
      <div class="col-md-4 col-sm-6" v-for="house in houses" :key="house.houseLink">
        <HouseCard :house="house" />
      </div>
    </div>
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
/* Personalización adicional si es necesario */
</style>
