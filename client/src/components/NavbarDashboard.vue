<template>
  <nav class="navbar navbar-dark fixed-top bg-dark flex-md-nowrap p-0 shadow">
    <a class="navbar-brand col-sm-3 col-md-2 mr-0" href="https://github.com/mickeystrike" target="_blank">E-Commerce CMS</a>
    <ul class="navbar-nav px-3">
      <li class="nav-item text-nowrap">
        <a class="nav-link btn" @click="logout">Sign Out</a>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  methods: {
    logout () {
      localStorage.clear()
      this.$router.push('/')
    }
  }
}
</script>

<style scoped>
.img-fluid {
  max-height: 50px;
}
</style>
