<template>
  <div>
    <router-link :to="houseLink" class="text-decoration-none">
      <div class="card text-center shadow-sm h-100">
        <div class="card-body">
          <h3 class="card-title h5">{{ house.House_name }}</h3>
          <p class="card-text">{{ house.Region }}</p>
        </div>
      </div>
    </router-link>
  </div>
</template>

<script>
export default {
  props: {
    house: {
      type: Object,
      required: true,
    },
  },
  computed: {
    houseLink() {
      // Generar dinámicamente el enlace para cada casa basado en el nombre
      return `/houses/${this.house.House_name.toLowerCase().replace(/\s+/g, '-')}`;
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

.card-title {
  color: #333;
}

.card-text {
  color: #555;
}
</style>
