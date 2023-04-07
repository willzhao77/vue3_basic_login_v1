<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div class="link">
      <nav>
        <RouterLink to="/" class="route-link">Home</RouterLink>
        <RouterLink to="/about" class="route-link">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style lang="scss" scoped>
@import url('./assets/reset.css');
nav {
  display: flex;
  .route-link {
  width: 150px;
  height: 50px;
  }
}

</style>
