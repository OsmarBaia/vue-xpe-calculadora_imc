<template>
  <h1>Cálculo IMC</h1>
  <h2>Digite seu peso e altura</h2>

  <span class="p-float-label">
	<InputText id="input-weight" type="text" v-model="weight" />
	<label for="input-weight">Peso</label>
  </span>

  <span class="p-float-label">
	<InputText id="input-height" type="text" v-model="height" />
	<label for="input-height">Peso</label>
  </span>
  <PrimeButton label="Calcular" />
</template>

<script>
export default {
  data() {
    return{
      height: null,
      weight: null
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


</style>
