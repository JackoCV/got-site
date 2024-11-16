<template>
    <div class="battle-card">
      <h3>{{ battle.name }}</h3>
      <p>Location: {{ battle.location }}</p>
      <NuxtLink :to="`/battles/${battle.id}`">
        <button>View Details</button>
      </NuxtLink>
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
  .battle-card {
    border: 1px solid #ddd;
    padding: 1rem;
    border-radius: 8px;
    text-align: center;
  }
  </style>
  