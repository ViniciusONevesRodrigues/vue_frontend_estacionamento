<template>
    <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/add">Add</router-link>
  </nav>
  <router-view/>
</template>

<script>
    export default {
        name: 'Navbar'
    }
</script>

<style scoped>
nav {
    background-color: azure;
    text-align: center;
    border-radius: 10px;
}

</style>