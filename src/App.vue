<template>
  <Header />
  <div class="container mx-auto bg-teal-100 px-3">
    <router-view/>
  </div>
</template>

<script>
  import Header from './components/Header.vue'
  export default {
    components: {
      Header
    }
  }
</script>

<style>

</style>
