<!--Main view of the Hermes-->
<template>
  <div class="home">
    <Header></Header>
    <div class="home-content">
      <div class="home-content-text">
        <h1>WELCOME TO HERMES</h1>
        <p>Here you can find the best deals for your next trip</p>
      </div>
      <Search/>
    </div>
  </div>
</template>

<script>
  import Header from '@/components/HeaderComponent.vue'
  import Search from '@/components/searchComponent.vue'
  export default {
  name: 'HomeView',
  components: {
    Header,
    Search
  }
}
</script>

<style scoped>

p{
  color: red;
}
</style>>
