<template>
    <nav class="navbar">
      <div class="logo">
        <img src="/logo.png" alt="Game of Thrones Logo" />
      </div>
      <ul class="nav-links">
        <li><NuxtLink to="/">Home</NuxtLink></li>
        <li><NuxtLink to="/characters">Characters</NuxtLink></li>
        <li><NuxtLink to="/houses">Houses</NuxtLink></li>
        <li><NuxtLink to="/battles">Battles</NuxtLink></li>
        <li><NuxtLink to="/episodes">Episodes</NuxtLink></li>
      </ul>
    </nav>
  </template>
  
  <style scoped>
  .navbar {
    display: flex;
    justify-content: space-between;
    padding: 1rem;
    background-color: #333;
    color: #fff;
  }
  .nav-links {
    list-style-type: none;
    display: flex;
    gap: 1rem;
  }
  </style>
  