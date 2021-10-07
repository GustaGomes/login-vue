<template>
    <h1> Home App</h1>
    <button v-on:click="logout">Logout</button>
</template>
<script>
export default {
    name:'Home',

    methods:{
        logout()
        {
            localStorage.clear();
            this.$router.push({ name: 'Login' })
        }
    },


    mounted()
    {
        let user = localStorage.getItem('user-info');
        if(!user)
        {
            this.$router.push({name:'SignUp'})
        }
    }

}
</script>