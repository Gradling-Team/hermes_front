<!--Login page-->
<template>
    <Header></Header>
    <div class="login">
        <div class="login-form">
        <h1>Login</h1>
        <form>
            <div class="form-group">
            <label for="email">Email</label>
            <input type="email" class="form-control" id="email" aria-describedby="emailHelp" placeholder="Enter email">
            </div>
            <div class="form-group">
            <label for="password">Password</label>
            <input type="password" class="form-control" id="password" placeholder="Password">
            </div>
            <button type="submit" class="btn btn-primary">Submit</button>
        </form>
        </div>
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

<style>

</style>