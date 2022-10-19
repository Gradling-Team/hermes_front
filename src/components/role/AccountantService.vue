<template>
    <div id="work">
        <h2>Accountant - Create a new order</h2>
        <div id="taskBoard">
            <div class="line">
                <div class="element" id="id">
                    <p>ID: {{task.id}}</p>
                </div>
                <div class="element" id="quantity">
                    <p>Quantity: {{task.quantity}}</p>
                </div>
            </div>
            <div class="line">
                <div class="element" id="from">
                    <p>Location: {{task.location}}</p>
                </div>
                <div class="element" id="dest">
                    <p>Dest: {{task.dest}}</p>
                </div>
            </div>
            <div class="line">
                <div  id="confirm">
                    <button @click="confirm" >Confirm</button>
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
            task:{
                id: 1,
                quantity: 1,
                location: "R748",
                dest: "R748",
            }

        }
    },
    methods:{
        confirm(){
            fetch('http://localhost:3000/confirm', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify(this.task)
            })
            fetch('http://localhost:3000/getTask', {method: 'GET'}).then((response) => response.json()).then(data => {
                this.task = data
            })
        },
        report(){
            fetch('http://localhost:3000/getTask', {method: 'GET'}).then((response) => response.json()).then(data => {
                this.task = data
            })
            console.log("report")
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