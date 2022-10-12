<template>
    <div id="search">
        <h2>research a product</h2>
        <div id="searchbare">
            <input type="text" id="searchbar" placeholder="Search">
            <button id="searchbutton">Search</button>
        </div>
        <div id="result">
            <div id="product" v-for="product in product" :key="product.id">
                {{product.id}}
                {{product.name}}
                {{product.lot}}
                {{product.storage}}
                {{product.peremption}}
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'searchComponent',
data(){
    return {
        products: [
            {id: 1, name: 'product 1', lot: 111, storage:"R748", peremption:"11/11/11" },
            {id: 1, name: 'product 1', lot: 111, storage:"R748", peremption:"11/11/11" },

        ]
    }
}
}
</script>

<style lang="scss" scoped>
#search{
    font-family: 'Orbitron', sans-serif;
    h2{
        text-align: center;
        font-size: 2em;
        font-weight: bold;
    }
    width: 60%;
    margin: auto;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: left;
    text-align: left;
    }
</style>