<template>
  <div id="reception">
    <h2>Admin - Post a new type of product</h2>
    <div id="taskBoard">
        <div class="line">
            <div class="element" id="name">
                <label>Enter a name:</label>
                <input type="text" id="productQuantity" placeholder="Quantity" v-model="product.name">
            </div>
            <div class="element" id="cost">
                <label>Enter a cost:</label>
                <input type="text" id="productID" placeholder="ID" v-model="product.cost">
            </div>
            <div class="element" id="retail">
                <label>Enter a retail number:</label>
                <input type="text" id="productQuantity" placeholder="Quantity" v-model="product.retail">
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
        name: {},
        quantity: 0,
        retail: 0,
      },
      data: {},
    };
  },
  methods: {
    confirm() {
      this.data = {
        name: this.product.name,
        cost: this.product.cost,
        retail: this.product.retail,
      };
      console.log(this.data);
      let xhr = new XMLHttpRequest();
      xhr.open("POST", "http://localhost:3000/productData", true);
      xhr.setRequestHeader("Content-Type", "application/json");
      xhr.setRequestHeader("accept", "application/json");
      xhr.send(JSON.stringify(this.data));
    },
  },
};
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