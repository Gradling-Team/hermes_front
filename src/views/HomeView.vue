<!--Main view of the Hermes-->
<template>
  <div class="home">
    <Header></Header>
    <div class="home-content">
      <div class="home-content-text">
        <h1>WELCOME TO HERMES</h1>
        <p>Here you can find the best deals for your next trip</p>
      </div>
    </div>
  </div>
</template>

<script>
  import Header from '@/components/HeaderComponent.vue'
  export default {
  name: 'HomeView',
  components: {
    Header
  }
}
</script>

<style scoped>

p{
  color: red;
}
</style>>
