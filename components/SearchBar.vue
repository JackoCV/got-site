<template>
  <div class="input-group p-3">
    <input
      type="text"
      class="form-control"
      v-model="query"
      placeholder="Search..."
      aria-label="Search"
    />
    <button class="btn btn-primary" type="button" @click="emitSearch">
      Search
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      query: '',
    };
  },
  methods: {
    emitSearch() {
      this.$emit('search', this.query);
    },
  },
};
</script>

<style scoped>
/* Personalización adicional si es necesario */
</style>
