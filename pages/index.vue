<template>
  <div>
    <!-- Barra de Navegación Global -->
    <NavBar />

    <!-- Acceso Rápido a las Diferentes Secciones -->
    <section class="quick-links container text-center mt-5">
      <h2 class="display-5 mb-4">Explore the World of Game of Thrones</h2>
      <div class="row">
        <div class="col-md-3 col-sm-6 mb-4" v-for="link in links" :key="link.path">
          <NuxtLink :to="link.path" class="card text-decoration-none shadow-sm h-100">
            <div class="card-body">
              <h3 class="card-title h5">{{ link.title }}</h3>
              <p class="card-text">{{ link.description }}</p>
            </div>
          </NuxtLink>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import NavBar from '~/components/NavBar.vue';

export default {
  name: 'IndexPage',
  components: {
    NavBar,
  },
  data() {
    return {
      links: [
        {
          path: '/characters',
          title: 'Characters',
          description: 'Meet the most iconic characters from Game of Thrones.',
        },
        {
          path: '/houses',
          title: 'Houses',
          description: 'Discover the noble houses of Westeros.',
        },
        {
          path: '/battles',
          title: 'Battles',
          description: 'Learn about the legendary battles fought in the realm.',
        },
        {
          path: '/episodes',
          title: 'Episodes',
          description: 'Explore episodes from all seasons of the series.',
        },
      ],
    };
  },
};
</script>

<style scoped>
/* Personaliza estilos aquí si es necesario */
.card {
  border-radius: 0.5rem;
  transition: transform 0.2s, box-shadow 0.2s;
}

.card:hover {
  transform: scale(1.05);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}
</style>
