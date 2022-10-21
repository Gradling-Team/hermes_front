<template>
    <div id="work">
        <h2>Accountant - Create a new order</h2>
        <div id="taskBoard">
            <div class="line">
                <div class="element" id="dest">
                    <label>Enter the destination:</label>
                    <input type="text" id="orderDestination" placeholder="Destination" v-model="order.destination">
                </div>
            </div>
            <div class="line">
                <div class="element" id="deliveryMonth">
                    <label>Enter the month:</label>
                    <input type="text" id="orderMonth" placeholder="Month" v-model="order.month">
                </div>
                <div class="element" id="deliveryDay">
                    <label>Enter the day:</label>
                    <input type="text" id="orderDay" placeholder="Day" v-model="order.day">
                </div>
                <div class="element" id="deliveryYear">
                    <label>Enter the year:</label>
                    <input type="text" id="orderYear" placeholder="Year" v-model="order.year">
                </div>
            </div>
            <div class="line">
                <div  id="confirm">
                    <button @click="confirm" >Confirm</button>
                    <!--when submitted send datenow and statuscode W-->
                </div>
                <div id="report">
                    <button @click="report">Report</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'WorkComponent',
    data(){
        return {
            order:{
                destination: "",
                month: null,
                day: null,
                year: null,
            }

        }
    },
    methods:{
        confirm(){
            fetch('/api/tickets/'+localStorage.getItem("token"), {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                    

                    DELIVERYDATE: this.order.day + "-"+ this.order.month +"-"+this.order.year+ " " +this.order.month + ":"+ this.order.month +":"+this.order.month ,
                    DESTINATION: this.order.destination
                })
            });

}
}
}
</script>

<style lang="scss" scoped>
#work{
    background-color: beige;
    display: flex;
    flex-direction: column;
    text-align: left;
    padding: 1em;
    #taskBoard{
        font-family: 'Orbitron', sans-serif;
        width: 100%;
        margin: auto;

        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: left;
        text-align: left;
        .line{
            display: flex;
            width: 100%;
            flex-direction: row;
            justify-content: center;
            text-align: left;
            .element{
                margin: 1em auto 1em auto;
                background-color: aliceblue;
                width: 30%;        
                input{
                    width: 100%;
                }        
            }
            #confirm, #report{
                text-align: center;
                margin: 1em auto 1em auto;
                width: 30%;        
            }
            p{
                margin: 0.3em;
            }
        }

    }
}

</style>