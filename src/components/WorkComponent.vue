<template>
    <div class="work">
        <h1> WorkSpace</h1>
        <DataProduct/>
        <WareHouseMan/>
        <ReceptionistMan/>

    </div>
</template>

<script>
import WareHouseMan from '@/components/role/WareHouseMan.vue'
import ReceptionistMan from './role/ReceptionistMan.vue'
import DataProduct from '@/components/DataProduct.vue'

export default {
    components: {
        WareHouseMan,
        ReceptionistMan,
        DataProduct
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