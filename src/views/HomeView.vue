<template>
  <div class="home">
    <ViewUser />
  </div>

  
  
  </template>

<script>
// @ is an alias to /src
import ViewUser from '@/components/ViewUser.vue'

export default {
  name: 'HomeView',
  components: {
    ViewUser
  }
}
</script>

<style scoped>
.input-container{
  float:right;
}
</style>
