<template>
    <div class="battle-list">
      <BattleCard
        v-for="battle in battles"
        :key="battle.battle_number"
        :battle="battle"
      />
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
  .battle-list {
    display: flex;
    flex-wrap: wrap;
    gap: 1.5rem;
    justify-content: center;
    margin-top: 2rem;
  }
  </style>
  