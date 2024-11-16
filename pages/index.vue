<template>
  <div>
    <!-- Barra de Navegación Global -->
    <NavBar />

    <!-- Acceso Rápido a las Diferentes Secciones -->
    <section class="quick-links">
      <h2>Explore the World of Game of Thrones</h2>
      <div class="links">
        <NuxtLink to="/characters" class="link-card">
          <h3>Characters</h3>
          <p>Meet the most iconic characters from Game of Thrones.</p>
        </NuxtLink>
        
        <NuxtLink to="/houses" class="link-card">
          <h3>Houses</h3>
          <p>Discover the noble houses of Westeros.</p>
        </NuxtLink>
        
        <NuxtLink to="/battles" class="link-card">
          <h3>Battles</h3>
          <p>Learn about the legendary battles fought in the realm.</p>
        </NuxtLink>
        
        <NuxtLink to="/episodes" class="link-card">
          <h3>Episodes</h3>
          <p>Explore episodes from all seasons of the series.</p>
        </NuxtLink>
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
};
</script>

<style scoped>
/* Estilos para la página principal */

.quick-links {
  padding: 2rem;
  text-align: center;
}

.links {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1.5rem;
  margin-top: 1rem;
}

.link-card {
  background: #f8f8f8;
  border-radius: 8px;
  padding: 1.5rem;
  width: 200px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  text-decoration: none;
  color: #333;
  transition: box-shadow 0.3s ease;
}

.link-card:hover {
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}
</style>
