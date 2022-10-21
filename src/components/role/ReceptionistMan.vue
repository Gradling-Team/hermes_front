<template>
    <div id="reception">
        <h2>Receptionnist - Add a new product</h2>
        <div id="taskBoard">
            <div class="line">
                <div class="element" id="id">
                    <label>Enter a reception ID:</label>
                    <input type="text" id="receptionID" placeholder="ID" v-model="reception.id">
                </div>
                <div class="element" id="statusCode">
                    <label>Enter the statuscode:</label>
                    <input type="text" id="receptionStatusCode" placeholder="Statuscode" v-model="reception.statuscode">
                </div>
            </div>
            <div class="line">
                <div class="element" id="source">
                    <label>Enter the source warehouse:</label>
                    <input type="text" id="receptionSource" placeholder="Source" v-model="reception.source">
                </div>
                <div class="element" id="destination">
                    <label>Enter the destination warehouse:</label>
                    <input type="text" id="receptionDestination" placeholder="Destination" v-model="reception.destination">
                </div>
            </div>
            <div class="line">
                <div  id="confirm">
                    <button @click="confirm">Confirm</button>
                    <!--when submitted send datenow-->
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
    name: 'ReceptionistMan',
    data(){
        return {
            reception:{
                id: 1,
                source: "R748",
                destination: "R748",
            },
            data:{}

        }
    },
    methods:{
        confirm(){
            fetch('http://localhost:3000/+ product.id', {methods:'GET'}).then((response) => response.json()).then(data => {
                this.data = data
            })
            fetch('http://localhost:3000/addProduct', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify(this.data)
            })
        }

    }

}
</script>

<style lang="scss" scoped>
#reception{
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