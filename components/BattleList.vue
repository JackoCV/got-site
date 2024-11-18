<template>
  <div class="container mt-4">
    <div class="row g-4">
      <div class="col-md-4 col-sm-6" v-for="battle in battles" :key="battle.battleLink">
        <BattleCard :battle="battle" />
      </div>
    </div>
  </div>
</template>

<script>
import BattleCard from './BattleCard.vue';

export default {
  props: {
    battles: {
      type: Array,
      required: true,
    },
  },
  components: {
    BattleCard,
  },
};
</script>

<style scoped>
/* Personalización adicional si es necesario */
</style>
