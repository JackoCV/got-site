<template>
    <div>
      <router-link v-if="character.characterLink" :to="{ name: 'characters-id', params: { id: character.characterLink.split('/').slice(-2, -1)[0] } }">
        <div class="character-card">
          <img v-if="character.image" :src="character.image" :alt="character.characterName" />
          <h3>{{ character.characterName }}</h3>
          <p v-if="character.houseName">House: {{ character.houseName }}</p>
          <p>{{ character.actorName }}</p>
        </div>
      </router-link>
      <div v-else class="character-card">
        <img v-if="character.image" :src="character.image" :alt="character.characterName" />
        <h3>{{ character.characterName }}</h3>
        <p v-if="character.houseName">House: {{ character.houseName }}</p>
        <p>{{ character.actorName }}</p>
      </div>
    </div>
  </template>
  
  
  
  <script>
  export default {
    props: {
      character: {
        type: Object,
        required: true,
      },
    },
  };
  </script>
  
  <style scoped>
  .character-card {
    background: #f8f8f8;
    border-radius: 8px;
    padding: 1.5rem;
    width: 200px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    text-align: center;
    transition: box-shadow 0.3s ease;
  }
  
  .character-card:hover {
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
  }
  
  .character-card img {
    width: 100%;
    height: auto;
    border-radius: 4px;
    margin-bottom: 1rem;
  }
  </style>
  