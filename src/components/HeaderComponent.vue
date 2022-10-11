<template>
    <header>
        <div id="logo" class="boxH">
            <img src="../assets/logo.png" alt="logo">
        </div>
        <div id="Hermes" class="boxH">
            <router-link to="/">Hermes-WMS</router-link>
        </div>
        <div id="login" class="boxH">
            <RouterLink to="login" class="button"><a>Login</a></RouterLink>
        </div>
    </header>
</template>

<script>
export default {
    name: 'HeaderComponent',
    components: {
    }

}
</script>

<style lang="scss" scoped>
header {
    display: flex;
    justify-content: space-around;
    align-items: center;
    height: 15vh;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    background-color: aliceblue;
    #Hermes {
        text-decoration: none;
        font-size: 2em;
        font-weight: bold;
        font-family: 'Orbitron', sans-serif;
        
    }
    #login{
        .button{
            height: 30%;
            width: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 1em;
            background-color: aliceblue;
            border: none;
            font-size: 16px;
            text-decoration: none;
            cursor: pointer;
        }
    }
    img{
        display: block;
        width: 12em;
        height: 7em;
    }
    .boxH{
        background-color: beige;
        width: 25%;
        height: 90%;
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 1em;
    }
}

</style>