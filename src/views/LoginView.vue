<!--Login page-->
<template>
    <Header></Header>
    <div class="login">
        <h1>Login</h1>
        <form>
            <div class="formGroup">
                <label for="ref">Warehouse referece</label>
                <input class="formControl" id="ref" required placeholder="reference">
            </div>
            <div class="formGroup">
                <label for="login">Login</label>
                <input class="formControl" id="login" required placeholder="login">
            </div>
            <div class="formGroup">
                <label for="password">Password</label>
                <input type="password" class="formControl" required id="password" placeholder="Password">
            </div>
            <button type="submit" class="btn">Login</button>
        </form>
    </div>
</template>

<script>
import Header from '@/components/HeaderComponent.vue'
export default {
    name: 'LoginView',
    components: {
        Header
    }

}
</script>

<style lang="scss" scoped>
.login{
    font-family: 'Orbitron', sans-serif;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 70vh;
    h1{
        font-size: 2em;
        font-weight: bold;
    }
    form{
        width: 30%;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        .formGroup{
            width: 100%;
            display: flex;
            flex-direction: column;
            text-align: left;
            justify-content: center;
            margin: 1em;
            label{
                
                font-size: 1.2em;
                font-weight: bold;
            }
            .formControl{
                width: 100%;
                height: 2em;
                border-radius: 0.5em;
                padding: 0.5em;
                border: none;
                font-size: 16px;
                text-decoration: none;
                background-color: aliceblue;
                cursor: pointer;
            }
        }
        .btn{
            height: 2em;
            width: 20em;
            border-radius: 1em;
            background-color: aliceblue;
            border: none;
            font-size: 16px;
            text-decoration: none;
            cursor: pointer;
        }
    }
}

</style>