<template>
    <div class="work">
        <h1> WorkSpace</h1>
        <WareHouseMan/>
    </div>
</template>

<script>
import WareHouseMan from '@/components/role/WareHouseMan.vue'

export default {
    components: {
         WareHouseMan 
        }
}
</script>

<style lang="scss" scoped>
h1{
    font-family: 'Orbitron', sans-serif;
}
.work{
    font-family: 'Orbitron', sans-serif;
    width: 60%;
    margin: auto;

  }

</style>