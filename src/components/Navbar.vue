<template>
  <div class="pure-menu pure-menu-horizontal">
    <div class="container">
      <a href="#" class="pure-menu-heading pure-menu-link">Home</a>
      <ul class="pure-menu-list">
        <li class="pure-menu-item"><router-link :to="{path: '/single'}" class="pure-menu-link">Upload</router-link>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Navbar"
  };
</script>

<style scoped>
  .pure-menu {
    background-color: #DB623D;
  }
  .pure-menu a {
    color: white;
  }
</style>