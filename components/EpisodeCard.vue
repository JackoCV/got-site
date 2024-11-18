<template>
  <div>
    <router-link v-if="episode.episodeLink" :to="episode.episodeLink" class="text-decoration-none">
      <div class="card text-center shadow-sm h-100">
        <div class="card-body">
          <h3 class="card-title h5">{{ episode.episodeTitle }}</h3>
          <p class="card-text"><strong>Season:</strong> {{ episode.seasonNum }}</p>
          <p class="card-text"><strong>Episode:</strong> {{ episode.episodeNum }}</p>
          <p class="card-text"><strong>Air Date:</strong> {{ episode.episodeAirDate }}</p>
          <p class="card-text"><strong>Description:</strong> {{ truncateDescription(episode.episodeDescription) }}</p>
          <p v-if="episode.openingSequenceLocations.length" class="card-text">
            <strong>Locations:</strong> {{ episode.openingSequenceLocations.join(', ') }}
          </p>
        </div>
      </div>
    </router-link>
    <div v-else class="card text-center shadow-sm h-100">
      <div class="card-body">
        <h3 class="card-title h5">{{ episode.episodeTitle }}</h3>
        <p class="card-text"><strong>Season:</strong> {{ episode.seasonNum }}</p>
        <p class="card-text"><strong>Episode:</strong> {{ episode.episodeNum }}</p>
        <p class="card-text"><strong>Air Date:</strong> {{ episode.episodeAirDate }}</p>
        <p class="card-text"><strong>Description:</strong> {{ truncateDescription(episode.episodeDescription) }}</p>
        <p v-if="episode.openingSequenceLocations.length" class="card-text">
          <strong>Locations:</strong> {{ episode.openingSequenceLocations.join(', ') }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    episode: {
      type: Object,
      required: true,
    },
  },
  methods: {
    // Truncar descripción para que no sea demasiado larga
    truncateDescription(description, maxLength = 100) {
      return description.length > maxLength ? description.slice(0, maxLength) + '...' : description;
    },
  },
};
</script>

<style scoped>
/* Personalización adicional */
.card {
  border-radius: 0.5rem;
  transition: transform 0.2s, box-shadow 0.2s;
  margin-bottom: 1rem;
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
  margin: 0.5rem 0;
}
</style>
