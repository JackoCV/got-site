<template>
    <div>
        <NavBar />

        <div class="container mt-4">
            <h1 class="display-4 text-center">Episodes</h1>
            <EpisodeList :episodes="episodes" />
        </div>
        <div v-if="episode" class="container mt-4">
            <!-- Información del episodio -->
            <div class="text-center mb-5">
                <h1 class="display-4">{{ episode.episodeTitle }}</h1>
                <p><strong>Season:</strong> {{ episode.seasonNum }}</p>
                <p><strong>Episode:</strong> {{ episode.episodeNum }}</p>
                <p><strong>Air Date:</strong> {{ episode.episodeAirDate }}</p>
                <p><strong>Description:</strong> {{ episode.episodeDescription }}</p>
                <p v-if="episode.openingSequenceLocations.length">
                    <strong>Opening Sequence Locations:</strong>
                    {{ episode.openingSequenceLocations.join(', ') }}
                </p>
            </div>

            <!-- Escenas -->
            <div>
                <h2 class="h4 mt-4 mb-4 text-center">Scenes</h2>
                <div class="row">
                    <div v-for="scene in scenes" :key="scene.sceneTitle" class="col-md-6 mb-4">
                        <div class="card shadow-sm">
                            <div class="card-body">
                                <h5 class="card-title"><strong>Location:</strong> {{ scene.location }}</h5>
                                <p class="card-text">
                                    <strong>Scene Start:</strong> {{ scene.sceneStart }}<br />
                                    <strong>Scene End:</strong> {{ scene.sceneEnd }}<br />
                                    <strong>Characters:</strong> {{ scene.characters.map((c) => c.name).join(', ') }}
                                </p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div v-else class="text-center mt-5">
            <p class="text-muted">Loading episode details...</p>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import Navbar from '@/components/Navbar.vue';


export default {
    components: {
        NavBar,
    },
    data() {
        return {
            episode: null,
            scenes: [],
        };
    },
    async fetch() {
        try {
            const episodeId = this.$route.params.id;

            const response = await axios.get('/characters/episodes.json');

            this.episode = response.data.find(
                (b) => `/episodes/${b.episodeTitle.replace(/\s+/g, '-')}` === `/episodes/${episodeId}`
            );

            this.scenes = this.episode.scenes;
        } catch (error) {
            console.error('Error loading episode:', error);
        }
    },
};
</script>

<style scoped>
/* Personaliza estilos aquí si es necesario */
.card {
    border-radius: 0.5rem;
}
</style>