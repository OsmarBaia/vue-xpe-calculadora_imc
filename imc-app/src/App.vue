<template>
  <h1>Cálculo IMC</h1>
  <h2>Digite seu peso e altura</h2>
  <div class="userInput">
    <span class="p-float-label">
      <InputText id="input-weight" type="text" v-model="weight" />
      <label for="input-weight">Peso</label>
    </span>
  </div>
  <div class="userInput">
     <span class="p-float-label">
       <InputText id="input-height" type="text" v-model="height" />
       <label for="input-height">Altura</label>
     </span>
  </div>
  <div class="btn-calc">
    <PrimeButton label="Calcular" @click="CalcularIMC"/>
  </div>

  <div class="imc-msg">
    <p>Seu IMC é: {{imc}}</p>
  </div>

</template>

<script>
export default {
  data() {
    return{
      height: null,
      weight: null,
      imc: null
    }
  },
  methods:{
    CalcularIMC: function (){
      this.imc = (this.weight/(this.height**2)).toFixed(2);
      console.log(this.imc);
    }
  }
}
</script>

<style>
/*#app {*/
/*  font-family: Avenir, Helvetica, Arial, sans-serif;*/
/*  -webkit-font-smoothing: antialiased;*/
/*  -moz-osx-font-smoothing: grayscale;*/
/*  color: #2c3e50;*/
/*}*/

.userInput{
  margin: 30px 10px;
}

PrimeButton{
  margin: 0 10px;
}
</style>
