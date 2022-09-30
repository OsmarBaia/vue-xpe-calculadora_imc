<!--HTML-->
<template>
  <h1 class="label-title">Cálculo IMC</h1>
  <h2 class="label-subtitle">Digite seu peso e altura</h2>
  <div class="userInput">
    <span class="p-float-label">
      <InputText id="input-weight" type="text" v-model="weight" :disabled="this.imc"/>
      <label for="input-weight">Peso</label>
    </span>
  </div>
  <div class="userInput">
     <span class="p-float-label">
       <InputText id="input-height" type="text" v-model="height" :disabled="this.imc"/>
       <label for="input-height">Altura</label>
     </span>
  </div>
  <div v-show="this.imc !== null" class="imc-msg label-subtitle">
    <p>Seu IMC é: {{imc}}</p>
  </div>
  <div v-show="this.classification !== null" class="feedback-msg label-subtitle">
    <p> A sua classificação com base no imc é: {{classification}}</p>
  </div>
  <div class="btn-calc">
    <PrimeButton v-if="this.classification === null" label="Calcular" @click="CalcularIMC"/>
    <PrimeButton v-else label="Limpar" @click="ResetValores"/>
  </div>
</template>

<!--JavaScript-->
<script>
export default {
  data() {
    return{
      height: null,
      weight: null,
      imc: null,
      classification: null,
    }
  },

  methods:{
    CalcularIMC: function (){
      this.imc = (this.weight/(this.height**2)).toFixed(2);
      this.CalcularClasse();
    },

    CalcularClasse: function (){
      if(this.imc < 18.5){
        this.classification = 'Magreza';
      }
      else if(this.imc >= 18.5 && this.imc < 25){
        this.classification = 'Normal';
      }
      else if(this.imc >= 25 && this.imc < 30){
        this.classification = 'Sobre Peso';
      }
      else if(this.imc >= 30 && this.imc < 40){
        this.classification = 'Obesidade';
      }else
      {
        this.classification = 'Obesidade Grave';
      }
    },

    ResetValores: function (){
      this.height = null;
      this.weight = null;
      this.imc = null;
      this.classification = null;
    }
  }
}
</script>

<!--CSS-->
<style>
*{
font-family: Avenir, Helvetica, Arial, sans-serif;
-webkit-font-smoothing: antialiased;
-moz-osx-font-smoothing: grayscale;
color: #2c3e50;
}

.userInput{
  margin: 2rem 0.1rem;
}

PrimeButton{
  margin: 0 0.1rem;
}

.label-title{
  font-size: 2rem;
}

.label-subtitle{
  font-size: 1.2rem;
}
</style>
