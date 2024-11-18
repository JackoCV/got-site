<template>
  <div>
    <NavBar />

    <div v-if="character" class="container mt-4">
      <div class="text-center">
        <h1 class="display-4">{{ character.characterName }}</h1>
        <img :src="character.characterImageFull" :alt="character.characterName" class="img-fluid rounded my-3"
          style="max-height: 400px;" />
        <p class="lead">{{ character.description }}</p>
        <p><strong>House:</strong> {{ character.houseName }}</p>
      </div>

      <div class="row">
        <div class="col-md-6">
          <h2 class="h4 mt-4">Parents</h2>
          <CharacterList :characters="parents" />
        </div>

        <div class="col-md-6">
          <h2 class="h4 mt-4">Siblings</h2>
          <CharacterList :characters="siblings" />
        </div>

        <div class="col-md-6">
          <h2 class="h4 mt-4">Married/Engaged To</h2>
          <CharacterList :characters="marriedEngaged" />
        </div>

        <div class="col-md-6">
          <h2 class="h4 mt-4">Served By</h2>
          <CharacterList :characters="servedBy" />
        </div>

        <div class="col-md-6">
          <h2 class="h4 mt-4">Parent Of</h2>
          <CharacterList :characters="parentOf" />
        </div>

        <div class="col-md-6">
          <h2 class="h4 mt-4">Killed By</h2>
          <CharacterList :characters="killedBy" />
        </div>

        <div class="col-md-6">
          <h2 class="h4 mt-4">Killed</h2>
          <CharacterList :characters="killed" />
        </div>

        <div class="col-md-6">
          <h2 class="h4 mt-4">Guarded By</h2>
          <CharacterList :characters="guardedBy" />
        </div>
      </div>
    </div>

    <div v-else class="text-center mt-5">
      <p class="text-muted">Loading character details...</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Navbar from '@/components/NavBar.vue';
import CharacterList from '~/components/CharacterList.vue';

export default {
  components: {
    NavBar,
    CharacterList
  },
  data() {
    return {
      character: null,
      parents: [],
      siblings: [],
      marriedEngaged: [],
      servedBy: [],
      parentOf: [],
      killedBy: [],
      killed: [],
      guardedBy: [],
    };
  },
  async fetch() {
    try {
      const id = this.$route.params.id;

      const response = await axios.get('/characters/characters.json');

      const characters = response.data.map((character, index) => ({
        ...character,
        characterLink: `/characters/${character.characterName.replace(/\s+/g, '-')}`
      }));

      this.character = characters.find(
        (b) => `/characters/${b.characterName.replace(/\s+/g, '-')}` === `/characters/${id}`
      );

      this.parents = characters.filter(
        (b) => b.parentOf?.includes(this.character.characterName)
      );

      this.siblings = characters.filter(
        (b) => b.siblings?.includes(this.character.characterName)
      );

      this.marriedEngaged = characters.filter(
        (b) => b.marriedEngaged?.includes(this.character.characterName)
      );

      this.servedBy = characters.filter(
        (b) => b.servedBy?.includes(this.character.characterName)
      );

      this.parentOf = characters.filter(
        (b) => b.parentOf?.includes(this.character.characterName)
      );

      this.killedBy = characters.filter(
        (b) => b.killedBy?.includes(this.character.characterName)
      );

      this.killed = characters.filter(
        (b) => b.killed?.includes(this.character.characterName)
      );

      this.guardedBy = characters.filter(
        (b) => b.guardedBy?.includes(this.character.characterName)
      );
    } catch (error) {
      console.error('Error loading character:', error);
    }
  },
};
</script>

<style scoped>
/* Personaliza el estilo aquí si es necesario */
</style>
