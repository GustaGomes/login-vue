<template>
  <!-- <Spinner start="spin.val" /> -->
  <router-view />
</template>

<script>
// import Spinner from './components/Spinner.vue'
export default {
  // components:{ Spinner },
  data:()=>({
    // spin: {
    //   val: true
    // }
  }),
  // provide(){
  //   return {
  //     appSpinner: this.spin
  //   };
  // }
}
</script>

<style>

body{
  margin: 0px;
}
.container {
  height: 100vh;
  display: flex;
  align-items: stretch;
}
.backgroungImg {
  flex: 1;
  background-size: cover;
  background: url("./assets/imgFront.png") no-repeat center;
}
.content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  max-width: 697px;
}
.content input {
  padding: 16px;
  width: 428px;
  color: #AFB8C0;
  display: flex;
  margin-top: 8px;
  outline: #AFB8C0;
  border: none;
  border-radius: 5px;
  background: var(--unnamed-color-ffffff) 0% 0% no-repeat padding-box;
  background: #FFFFFF 0% 0% no-repeat padding-box;
  box-shadow: 0px 0px 12px #00000029;
}
::placeholder {
  color: #AFB8C0;
  opacity: 1; 
}

.content button {
  background: transparent linear-gradient(90deg, #0046f5 0%, #0034b7 100%) 0% 0% no-repeat padding-box;
  height: 42px;
  border-radius: 12px;
  padding: 0 16px;
  width: 460px;
  font-weight: 500;
  margin-top: 16px;
  text-align: center;
  letter-spacing: 0.98px;
  color: #FFFFFF;
  opacity: 1;
}
.routerLink{
  text-decoration: none;
  color: #0045E6;
}

.component-login__input, .component-signUp__input {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  margin-top: 10px;
  font: var(--unnamed-font-style-normal) normal var(--unnamed-font-weight-normal) 14px/17px var(--unnamed-font-family-usual);
  color: var(--unnamed-color-141414);
  text-align: left;
  font: normal normal normal 14px/17px Usual;
  letter-spacing: 0.7px;
  color: #141414;
  opacity: 1;
}

</style>
