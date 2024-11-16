    <template>
        <div v-if="character">
        <h1>{{ character.characterName }}</h1>
        <img :src="character.image" :alt="character.characterName" />
        <p>{{ character.description }}</p>
        <p><strong>House:</strong> {{ character.houseName }}</p>
        <!-- Agrega más detalles del personaje aquí -->
        </div>
        <div v-else>
        <p>Loading character details...</p>
        </div>
    </template>
    
    <script>
    import axios from 'axios';
    
    export default {
        data() {
        return {
            character: null,
        };
        },
        async fetch() {
  try {
    // Obtener el ID del personaje desde la ruta
    const id = this.$route.params.id;

    // Cargar los datos de personajes
    const response = await axios.get('/characters/characters.json');

    // Buscar el personaje por characterLink que contenga el ID
    this.character = response.data.characters.find((char) =>
      char.characterLink.includes(id)
    );
  } catch (error) {
    console.error('Error loading character:', error);
  }
}
,
    };
    </script>
    
    <style scoped>
    /* Agrega estilos para la página de detalles */
    </style>
    