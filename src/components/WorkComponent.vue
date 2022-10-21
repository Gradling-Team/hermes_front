<template>
    <div class="work">
        <h1> WorkSpace</h1>
        <DataProduct/>
        <WareHouseMan/>
        <ReceptionistMan/>
        <DeliveryMan/>
        
        <Accountant/>

    </div>
</template>

<script>
import WareHouseMan from '@/components/role/WareHouseMan.vue'
import ReceptionistMan from './role/ReceptionistMan.vue'
import DataProduct from '@/components/role/DataProduct.vue'
import DeliveryMan from '@/components/role/DeliveryMan.vue'
import Accountant from '@/components/role/AccountantService.vue'

export default {
    components: {
        WareHouseMan,
        ReceptionistMan,
        DataProduct,
        DeliveryMan,
        Accountant,
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