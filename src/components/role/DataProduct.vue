<template>
  <div id="reception">
    <h2>Admin - Post a new type of product</h2>
    <div id="taskBoard">
        <div class="line">
            <div class="element" id="name">
                <label>Enter a name:</label>
                <input type="text" id="productQuantity" placeholder="Nom" v-model="product.name">
            </div>
            <div class="element" id="cost">
                <label>Enter a cost:</label>
                <input type="text" id="productID" placeholder="COST" v-model="product.cost">
            </div>
            <div class="element" id="retail">
                <label>Enter price:</label>
                <input type="text" id="productPrice" placeholder="PRICE" v-model="product.price">
            </div>
        </div>
        <div class="line">
            <div  id="confirm">
                <button @click="confirm">Confirm</button>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ReceptionistMan",
  data() {
    return {
      product: {
        name: "",
        cost: null,
        price: null,
      },
      data: {},
    };
  },
  methods: {
    confirm() {
      fetch('/api/product/'+localStorage.getItem("token"), {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify({
          Nom: this.product.name,
          COST: this.product.cost,
          PRICE: this.product.price
        })
    });
  },
}}
</script>

<style lang="scss" scoped>
#reception {
  background-color: beige;
  display: flex;
  flex-direction: column;
  text-align: left;
  padding: 1em;
  #taskBoard {
    font-family: "Orbitron", sans-serif;
    width: 100%;
    margin: auto;

    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: left;
    text-align: left;
    .line {
      display: flex;
      width: 100%;
      flex-direction: row;
      justify-content: center;
      text-align: left;
      .element {
        margin: 1em auto 1em auto;
        background-color: aliceblue;
        width: 30%;
        input {
          width: 100%;
        }
      }
      #confirm,
      #report {
        text-align: center;
        margin: 1em auto 1em auto;
        width: 30%;
      }
      p {
        margin: 0.3em;
      }
    }
  }
}
</style>