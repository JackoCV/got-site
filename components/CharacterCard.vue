<template>
  <div>
    <router-link v-if="character.characterLink" :to="character.characterLink" class="text-decoration-none">
      <div class="card text-center shadow-sm h-100">
        <img
          v-if="character.characterImageThumb"
          :src="character.characterImageThumb"
          :alt="character.characterName"
          class="card-img-top"
          style="max-height: 200px; object-fit: cover;"
        />
        <div class="card-body">
          <h3 class="card-title h5">{{ character.characterName }}</h3>
          <p v-if="character.houseName" class="card-text"><strong>House:</strong> {{ character.houseName }}</p>
          <p class="card-text">{{ character.actorName }}</p>
        </div>
      </div>
    </router-link>
    <div v-else class="card text-center shadow-sm h-100">
      <img
        v-if="character.characterImageThumb"
        :src="character.characterImageThumb"
        :alt="character.characterName"
        class="card-img-top"
        style="max-height: 200px; object-fit: cover;"
      />
      <div class="card-body">
        <h3 class="card-title h5">{{ character.characterName }}</h3>
        <p v-if="character.houseName" class="card-text"><strong>House:</strong> {{ character.houseName }}</p>
        <p class="card-text">{{ character.actorName }}</p>
      </div>
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
/* Personalización adicional */
.card {
  border-radius: 0.5rem;
  transition: transform 0.2s, box-shadow 0.2s;
}

.card:hover {
  transform: scale(1.05);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}
</style>
