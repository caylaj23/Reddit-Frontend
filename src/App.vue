<script setup>
import { RouterLink, RouterView } from 'vue-router';






</script>



<template>
    <header>
        <nav>
        <div class="nav-items">
          <RouterLink class="nav" to="/">Home</RouterLink>
          <RouterLink class="nav" to="/post">New Post</RouterLink>
        </div>
      </nav>

    </header>
  <RouterView/>
</template>

<style scoped>
.nav-items {
    display: flex;
    justify-content: space-between;
}

.nav {
    color: black;
}


</style>

