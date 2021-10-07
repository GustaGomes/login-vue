<template>
  <container class="container">
    <backgroung class="backgroungImg" />

    <content class="content">
      <img alt="Aires logo" src="../assets/logo.svg" />

      <div class="component-login__header--form">
        <h1>Acesso vie e-mail</h1>
        <p>Acesse sua conta Aires por algum método abaixo</p>
      </div>
      <div class="component-login__input">
        <label> Email </label>
        <input type="text" v-model="email" placeholder="Enter Email" />
      </div>
      <div class="component-login__input">
        <label> Passowrd </label>
        <input type="password" v-model="password" placeholder="Enter Password" />
      </div>
      <div class="component-login__input--connected">
        <div class="component-login__checkbox--connected">
            <input type="checkbox" id="" name="connected" value="connected">
            <label for="connected"> Continuar Conectado</label>
        </div>

        <router-link class="routerLink" to="/">Esqueceu sua senha?</router-link>
      </div>
      <button v-on:click="login">Acessar</button>

      <p>
        Não possui uma conta?
        <router-link class="routerLink" to="/sign-up"> Clique para criar sua conta</router-link>
      </p>
    </content>
  </container>
</template>
<script>
import axios from "axios";
export default {
  name: "Login",
  inject: ["appSpinner"],
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    async login() {
      let result = await axios.get(
        `http://localhost:3000/users?email=${this.email}&password=${this.password}`
      );

      if (result.status == 200 && result.data.length > 0) {
        localStorage.setItem("user-info", JSON.stringify(result.data[0]));
        this.$router.push({ name: "Home" });
      } else {
        alert("Usuario invalido");
      }
    },
  },
};
</script>

<style>
.component-login__input--connected{
    display: flex;
    align-items: center;
    margin-top: 10px;
    justify-content: space-between;
    width: 428px;
}
.component-login__input--connected input{
    width: 26px;
    height: 26px;
    background: #0A50D7 0% 0% no-repeat padding-box;
    border-radius: 3px;
    opacity: 1;
}
.component-login__input--connected label{

    text-align: left;
    font: normal normal normal 14px/17px Usual;
    letter-spacing: 0.7px;
    color: #141414;
}
.component-login__checkbox--connected{
    display: flex;
    align-items: center;
}

.component-login__header--form{
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    width: 460px;
    margin-top: 60px;
}
.component-login__header--form h1{
    margin: 0;
}
.component-login__header--form p{
    letter-spacing: 1.12px;
    color: #AFB8C0;
    opacity: 1;
}

         
</style>