<template>
  <div class="container mt-4">
    <div class="row g-4">
      <div class="col-md-4 col-sm-6" v-for="character in characters" :key="character.characterLink">
        <CharacterCard :character="character" />
      </div>
    </div>
  </div>
</template>

<script>
import CharacterCard from './CharacterCard.vue';

export default {
  props: {
    characters: {
      type: Array,
      required: true,
    },
  },
  components: {
    CharacterCard,
  },
};
</script>

<style scoped>
/* Personalización adicional si es necesario */
</style>
