<template>
  <div id="app">
    <h1>Jogo da Forca Vue.JS</h1>

    <section id="inicio" v-if="tela === 'inicio'">
     
    </section>

    <section id="jogo" v-if="tela === 'jogo'">
      
    </section>
  </div>
</template>

<script>
import "./css/global.css";

export default {
  name: "App",
  data() {
    return {
      tela: "inicio",
    };
  },
  components: {
  
  },
  methods: {
  
  },
};
</script>

<style>
#app {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
