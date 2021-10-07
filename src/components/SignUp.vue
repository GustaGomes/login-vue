<template>
    <container class="container">

        <backgroung class="backgroungImg"/>

        <content class="content">
                <img alt="Aires logo" src="../assets/logo.svg">

                <div class="component-signUp__header--form">
                    <h1> Crie sua conta</h1>
                    <p>Crie sua conta Aires</p>
                </div>
                <div class="component-signUp__input">
                    <label> Email </label>
                    <input type="text" v-model="email" placeholder="Enter Email">
                </div>
                <div class="component-signUp__input">  
                    <label> Name </label>
                    <input type="text" v-model="name" placeholder="Enter Name">
                </div>
                <div class="component-signUp__input">
                    <label> Password </label>
                    <input type="password" v-model="password" placeholder="Enter Password">
                </div>

                <button v-on:click="signUp"> Criar conta </button>


                <p>Já possui uma conta? <router-link class="routerLink" to="/login"> Clique para acessar</router-link></p>

                <p><router-link class="routerLink" to=""> Esqueceu sua senha?</router-link></p>
        </content>
    </container>

</template>

<script>
import axios from 'axios'

export default {
    name:'SignUp',
    data()
    {
        return {
            name: '',
            email: '',
            password: ''
        }
    },
    methods:{
        async signUp()
        {
            let result = await axios.post("http://localhost:3000/users",{
                email:this.email,
                password:this.password,
                name:this.name
            });

            console.log(result);
            if(result.status == 201)
            {
                localStorage.setItem("user-info", JSON.stringify(result.data))
                alert("Usuario cadastrado com sucesso")
                this.$router.push({name: 'Login'})
            }
        }
    },
    mounted()
    {
        let user= localStorage.getItem('user-info');
        if(user)
        {
            this.$router.push({name:'Home'})
        }
    }
}
</script>

<style>
.component-signUp__header--form{
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    width: 460px;
    margin-top: 60px;
}
.component-signUp__header--form h1{
    margin: 0;
}
.component-signUp__header--form p{
    letter-spacing: 1.12px;
    color: #AFB8C0;
    opacity: 1;
} 
</style>