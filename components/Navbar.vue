<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container-fluid">
      <NuxtLink to="/" class="navbar-brand d-flex align-items-center">
        <img src="/logo.png" alt="Game of Thrones Logo" style="height: 40px; margin-right: 10px;" />
        <span>Game of Thrones</span>
      </NuxtLink>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item">
            <NuxtLink to="/" class="nav-link">Home</NuxtLink>
          </li>
          <li class="nav-item">
            <NuxtLink to="/characters" class="nav-link">Characters</NuxtLink>
          </li>
          <li class="nav-item">
            <NuxtLink to="/houses" class="nav-link">Houses</NuxtLink>
          </li>
          <li class="nav-item">
            <NuxtLink to="/battles" class="nav-link">Battles</NuxtLink>
          </li>
          <li class="nav-item">
            <NuxtLink to="/episodes" class="nav-link">Episodes</NuxtLink>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<style scoped>
/* Puedes personalizar estilos adicionales aquí si es necesario */
</style>
