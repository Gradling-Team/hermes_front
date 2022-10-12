<template>
    <div id="search">
        <h2>research a product</h2>
        <div id="searchPlace">
            <div id="searchById">
                <div class="searchBare">
                    <label>Enter a product ID:</label>
                    <input type="text" id="searchbar" placeholder="Search" v-model="id">
                    <button id="searchbutton" @click="searchID" >Search</button>
                </div>
                <div v-if="displayIDResult" class="result">
                        {{IDResult.id}}
                        {{IDResult.name}}
                        {{IDResult.lot}}
                        {{IDResult.storage}}
                        {{IDResult.peremption}}
                </div>
                <div v-else class="result">
                    <p>No result</p>
                </div>
            </div>
            <div id="searchByName">
                <div class="searchBare">
                    <label>Enter a product Name:</label>
                    <input type="text" id="searchbar" placeholder="Search" v-model="name">
                    <button id="searchbutton" @click="searchName">Search</button>
                </div>
                <div class="result">
                    <div id="product" v-for="product in nameResult" :key="product.id">
                        <p :v-if="displayNameResult">
                            {{product.id}}
                            {{product.name}}
                            {{product.lot}}
                            {{product.storage}}
                            {{product.peremption}}
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'searchComponent',
    data(){
        return {
            nameResult: [
                {id: 1, name: 'product 1', lot: 111, storage:"R748", peremption:"11/11/11" },
                {id: 2, name: 'product 1', lot: 111, storage:"R748", peremption:"11/11/11" },],
            displayNameResult: false,
            name:"",
            IDResult:{id: 1, name: 'product 1', lot: 111, storage:"R748", peremption:"11/11/11" },
            displayIDResult: false,
            id:""
        }
    },
    methods:{
        searchID(){
            this.DisplayIDResult = true 
            console.log('http://localhost:3000/EP/'+this.id)
            
            fetch('http://localhost:3000/EP/' + this.id,{method: 'GET'}).then((response) => response.json()).then(data => {
                return console.log(JSON.stringify(data))
            })

        },
        searchName(){
            this.DisplayNameResult = true
            console.log("searchName")
            console.log('http://localhost:3000/EP/' + this.name,)
            fetch('http://localhost:3000/EP/' + this.name,{method: 'GET'}).then((response) => response.json()).then(data => {
                this.nameResult = data
            })
        },
    }
}
</script>

<style lang="scss" scoped>
#search{
    font-family: 'Orbitron', sans-serif;
    width: 60%;
    margin: auto;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: left;
    text-align: left;
    p{
        margin: 0.3em;
    }
    h2{
        text-align: center;
        font-size: 2em;
        font-weight: bold;
    }
    #searchPlace{
        background-color: beige;
        padding: 1em;
        .searchBare{
            margin: 0.5em;
        }
        label{
            margin-right: 1em;
        }
    }
    .result{
        padding: 1em;
        background-color: aliceblue;
    }
    }
</style>