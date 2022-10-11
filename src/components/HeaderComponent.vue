<template>
    <header>
        <div class="logo">
            <img src="../assets/logo.png" alt="logo">
        </div>
        <div class="Hermes">
        </div>
        <div class="login">
            <button>Login</button>
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

<style scoped>
header {
    display: flex;
    justify-content: space-around;
    align-items: center;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}
.logo{
    display: inline-block;
    width: 10em;
    height: 10em;
}
img{
    display: block;
    width: 90%;
}
</style>