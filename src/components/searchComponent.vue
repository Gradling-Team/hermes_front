<template>
  <div id="search">
    <h2>research a product</h2>
    <div id="searchPlace">
      <div id="searchById">
        <div class="searchBare">
          <label>Enter a product ID:</label>
          <input type="text" id="searchbar" placeholder="Search" v-model="id" />
          <button id="searchbutton" @click="searchID">Search</button>
        </div>
        <div v-if="displayIDResult" class="result">
          {{ IDResult.ID_Ep }}
          {{ IDResult.ID_prod }}
          {{ IDResult.ID_lot }}
          {{ IDResult.ID_ORDER }}
          {{ IDResult.ID_AREA }}
        </div>
        <div v-else class="result">
          <p>No result</p>
        </div>
      </div>
      <div id="searchByName">
        <div class="searchBare">
          <label>Enter a product Name:</label>
          <input
            type="text"
            id="searchbar"
            placeholder="Search"
            v-model="name"
          />
          <button id="searchbutton" @click="searchName">Search</button>
        </div>
        <div class="result">
          <div id="product" v-for="product in nameResult" :key="product.id">
            <p v-if="nameResult != 'unauthorized'">
              {{ product.ID_prod }} | {{ product.Nom }} | Price :
              {{ product.PRICE }}$ | Cost : {{ product.COST }}$ |
            </p>
          </div>
          <div v-if="nameResult === 'wrong'" id="product">No result</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "searchComponent",
  data() {
    return {
      nameResult: [],
      name: "",
      IDResult: [],
      displayIDResult: false,
      id: "",
    };
  },
  methods: {
    searchID() {
        this.DisplayIDResult = true;
        console.log("searchID");
        console.log("/api/ep/");
        fetch("/api/ep/" + localStorage.getItem("token") + "/" + this.name, {
          method: "GET",
        })
          .then((response) => response.json())
          .then((data) => {
            this.nameResult = data;
            console.log(data);
            if(this.nameResult.length > 0 ){
              this.displayIDResult = true;
            }
          });
      },
    searchName() {
      console.log("searchName");
      console.log("/api/product/");
      // get item from api
    
        fetch(
          "/api/product/" + localStorage.getItem("token") + "/" + this.name,
          { method: "GET" }
        )
          .then((response) => response.json())
          .then((data) => {
            this.nameResult = data;
            if (data != 'Token not found' && data != 'Token expired' && data != 'unauthorized') {
              console.log(data);
            } else if (data === 'Token expired') {
              alert("session expired");
              this.nameResult = 'wrong';
            }else{
              alert("Invalid Token");
              this.nameResult = 'wrong';
            }
          });
        
    },
  },
};
</script>

<style lang="scss" scoped>
#search {
  font-family: "Orbitron", sans-serif;
  width: 60%;
  margin: auto;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: left;
  text-align: left;
  p {
    margin: 0.3em;
  }
  h2 {
    text-align: center;
    font-size: 2em;
    font-weight: bold;
  }
  #searchPlace {
    background-color: beige;
    padding: 1em;
    .searchBare {
      margin: 0.5em;
    }
    label {
      margin-right: 1em;
    }
  }
  .result {
    padding: 1em;
    background-color: aliceblue;
  }
}
</style>