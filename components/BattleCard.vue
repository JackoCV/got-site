<template>
  <div>
    <router-link v-if="battle.battleLink" :to="battle.battleLink">
      <div class="battle-card">
        <h3>{{ battle.name }}</h3>
        <p><strong>Location:</strong> {{ battle.location }}</p>
        <p><strong>Year:</strong> {{ battle.year }}</p>
        <p><strong>Region:</strong> {{ battle.region }}</p>
      </div>
    </router-link>
  </div>
</template>

<script>
export default {
  props: {
    battle: {
      type: Object,
      required: true,
    },
  },
  computed: {
    battleLink() {
      return `/battles/${this.battle.battle_number}`;
    },
  },
};
</script>

<style scoped>
.battle-card {
  background: #f8f8f8;
  border-radius: 8px;
  padding: 1.5rem;
  width: 200px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  text-align: center;
  transition: box-shadow 0.3s ease;
}
.battle-card:hover {
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}
</style>
