<!--Main view of the Hermes-->
<template>
  <div class="home">
    <Header/>
    <Work/>
    <Search/>
  </div>
</template>

<script>
  import Header from '@/components/HeaderComponent.vue'
  import Search from '@/components/searchComponent.vue'
  import Work from '@/components/WorkComponent.vue'
  export default {
  name: 'HomeView',
  components: {
    Header,
    Search,
    Work
  }
}
</script>

<style scoped>

p{
  color: red;

}
</style>>
