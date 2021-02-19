<template>
  <div id="app">
    <h1>Converosor de Moedas</h1>
    <div class="linha">
      <conversor moeda-a="USD" moeda-b="BRL"/>
      <conversor moeda-a="BRL" moeda-b="USD"/>
    </div>

    <div class="linha">
      <conversor moeda-a="EUR" moeda-b="BRL"/>
      <conversor moeda-a="BRL" moeda-b="EUR"/>
    </div>

    <footer>
      <div class="dev">
        by Kelvyn Reis
      </div>
    </footer>
    
  </div>
</template>


<script>
import Conversor from "./components/Conversor.vue";
export default {
  name: 'App',
  components: {
    Conversor
  }
}
</script>

<style>
#app {
  margin: auto;
  width: 900px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #402c50;
  margin-top: 60px;
}
.linha{
  margin-top: 40px;

  display:flex;
  justify-content: space-around;
}
footer{
  text-align: center;
  padding: 4rem 0 2rem;
  opacity: 0.6;
}
.dev{
  
}
</style>
