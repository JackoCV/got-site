<template>
  <div>
    <router-link v-if="battle.battleLink" :to="battle.battleLink" class="text-decoration-none">
      <div class="card text-center shadow-sm mb-3">
        <div class="card-body">
          <h3 class="card-title h5">{{ battle.name }}</h3>
          <p class="card-text"><strong>Year:</strong> {{ battle.year }}</p>
          <p class="card-text"><strong>Region:</strong> {{ battle.region }}</p>
          <p class="card-text"><strong>Location:</strong> {{ battle.location }}</p>
        </div>
      </div>
    </router-link>
    <div v-else class="card text-center shadow-sm mb-3">
      <div class="card-body">
        <h3 class="card-title h5">{{ battle.name }}</h3>
        <p class="card-text"><strong>Year:</strong> {{ battle.year }}</p>
        <p class="card-text"><strong>Region:</strong> {{ battle.region }}</p>
        <p class="card-text"><strong>Location:</strong> {{ battle.location }}</p>
      </div>
    </div>
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
};
</script>

<style scoped>
/* Personalización adicional para las tarjetas */
.card {
  border-radius: 0.5rem;
  transition: transform 0.2s, box-shadow 0.2s;
}

.card:hover {
  transform: scale(1.05);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

.card-title {
  color: #333;
}

.card-text {
  color: #555;
}
</style>
