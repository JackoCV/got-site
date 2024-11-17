<template>
  <div>
    <router-link :to="houseLink">
      <div class="house-card">
        <h3>{{ house.House_name }}</h3>
        <p>{{ house.Region }}</p>
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
.house-card {
  background: #f8f8f8;
  border-radius: 8px;
  padding: 1.5rem;
  width: 200px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  text-align: center;
  transition: box-shadow 0.3s ease;
}

.house-card:hover {
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}
</style>
