<template>
  <div>
    <!-- Barra de navegación -->
    <NavBar />

    <div v-if="battle" class="container mt-4">
      <!-- Título y detalles principales -->
      <div class="text-center mb-5">
        <h1 class="display-4">{{ battle.name }}</h1>
        <p class="lead"><strong>Year:</strong> {{ battle.year }}</p>
        <p><strong>Battle Number:</strong> {{ battle.battle_number }}</p>
        <p><strong>Region:</strong> {{ battle.region }}</p>
        <p><strong>Location:</strong> {{ battle.location }}</p>
      </div>

      <!-- Detalles adicionales -->
      <div class="row g-4">
        <div class="col-md-6">
          <h2 class="h5 text-center">Attacker King</h2>
          <CharacterList :characters="attacker_king" />
        </div>
        <div class="col-md-6">
          <h2 class="h5 text-center">Defender King</h2>
          <CharacterList :characters="defender_king" />
        </div>
        <div class="col-md-6">
          <h2 class="h5 text-center">Attackers</h2>
          <CharacterList :characters="attackers" />
        </div>
        <div class="col-md-6">
          <h2 class="h5 text-center">Defenders</h2>
          <CharacterList :characters="defenders" />
        </div>
      </div>
    </div>

    <div v-else class="text-center mt-5">
      <p class="text-muted">Loading battle details...</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Navbar from '@/components/Navbar.vue';
import CharacterList from '~/components/CharacterList.vue';

export default {
  components: {
    NavBar,
    CharacterList,
  },
  data() {
    return {
      battle: null,
      attacker_king: [],
      defender_king: [],
      attackers: [],
      defenders: [],
    };
  },
  async fetch() {
    try {
      const link = this.$route.params.id;

      const response = await axios.get('/battles/battles.json');
      const charactersResponse = await axios.get('/characters/characters.json');
      const charactersGroupsResponse = await axios.get('/characters/characters-groups.json');

      this.battle = response.data.find(
        (b) => `/battles/${b.name.replace(/\s+/g, '-')}` === `/battles/${link}`
      );

      this.attacker_king = charactersResponse.data.filter(
        (c) => c.characterName === this.battle.attacker_king
      );

      this.defender_king = charactersResponse.data.filter(
        (c) => c.characterName === this.battle.defender_king
      );

      const NameListAttackers = charactersGroupsResponse.data.filter((group) =>
        group.name === this.battle.attacker_1 ||
        group.name === this.battle.attacker_2 ||
        group.name === this.battle.attacker_3 ||
        group.name === this.battle.attacker_4 ||
        group.name === this.battle.attacker_commander_1 ||
        group.name === this.battle.attacker_commander_2 ||
        group.name === this.battle.attacker_commander_3 ||
        group.name === this.battle.attacker_commander_4
          ? group.characters
          : null
      );
      this.attackers = NameListAttackers[0]?.characters.map((name) =>
        charactersResponse.data.find((c) => c.characterName === name)
      );

      const NameListDefenders = charactersGroupsResponse.data.filter((group) =>
        group.name === this.battle.defender_1 ||
        group.name === this.battle.defender_2 ||
        group.name === this.battle.defender_3 ||
        group.name === this.battle.defender_4 ||
        group.name === this.battle.defender_commander_1 ||
        group.name === this.battle.defender_commander_2 ||
        group.name === this.battle.defender_commander_3 ||
        group.name === this.battle.defender_commander_4
          ? group.characters
          : null
      );
      this.defenders = NameListDefenders[0]?.characters.map((name) =>
        charactersResponse.data.find((c) => c.characterName === name)
      );
    } catch (error) {
      console.error('Error loading battle:', error);
    }
  },
};
</script>

<style scoped>
/* Estilos adicionales */
h1 {
  color: #333;
}

.text-center p {
  color: #555;
}

h2 {
  margin-bottom: 1rem;
}

.container {
  padding: 2rem;
}

.row {
  margin-bottom: 2rem;
}
</style>
