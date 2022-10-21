<template>
  <div id="work">
    <h2>Warehouseman - Tasks</h2>
    <div id="taskBoard">
      <div class="line">
        <div class="element" id="dest">
          <label>Enter the ID:</label>
          <input type="text" id="ID" placeholder="ID" v-model="id" />
        </div>
      </div>
      <div class="line">
        <div id="confirm">
          <button @click="confirm">Confirm</button>
        </div>
        <div id="report">
          <button @click="report">Report</button>
        </div>
      </div>
      <div class="line">
        <div class="result">
        <div v-if="displayIDResult">
        <div v-for="order in IDResult" :key="order.ID_ORDER" >
            <p>ID | Date creation | Status | Destination | Estimate Date </p>
                {{ order.ID_ORDER }} |
                {{ order.DATETIME }} |
                {{ order.STATUSCODE }} |
                {{ order.DESTINATION }} |
                {{ order.DELIVERYDATE }}
        </div>
        </div>
        <div v-else>
          <p>No result</p>
        </div>
    </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "WorkComponent",
  data() {
    return {
      IDResult: [],
      displayIDResult: false,
      id: "",
    };
  },
  methods: {
    confirm() {
      fetch("/api/warehouse/" + localStorage.getItem("token") + "/" + this.id, {
        method: "GET",
    })
    .then((response) => response.json())
    .then((data) => {
          this.IDResult = data;
          console.log(data);
          if (this.IDResult.length >= 1) {
            this.displayIDResult = true;
          }
        });
    },
    report() {
      fetch("/api/getTask", { method: "GET" })
        .then((response) => response.json())
        .then((data) => {
          this.task = data;
        });
      console.log("report");
    },
  },
};
</script>

<style lang="scss" scoped>
#work {
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
      }
      .result {
        padding: 1em;
        background-color: aliceblue;
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