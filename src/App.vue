<template>
  <div id="app">
    <h1>Jogo da Forca Vue.JS</h1>

    <section id="inicio" v-if="tela === 'inicio'">
      <FormularioJogo
        v-if="etapa === 'palavra'"
        title="Defina a palavra do jogo:"
        button="Próximo"
        :action="setPalavra"
      />

      <FormularioJogo
        v-if="etapa === 'dica'"
        title="Defina a dica: "
        button="Iniciar o jogo"
        :action="setDica"
      />
    </section>

    <section id="jogo" v-if="tela === 'jogo'">
      <InicioJogo
        :erros="erros"
        :palavra="palavra"
        :dica="dica"
        :verificarLetra="verificarLetra"
        :etapa="etapa"
        :letras="letras"
        :jogar="jogar"
        :jogarNovamente="jogarNovamente"
      />
    </section>
  </div>
</template>

<script>
import "./css/global.css";
import FormularioJogo from "./components/FormularioJogo.vue";
import InicioJogo from "./components/InicioJogo.vue";
export default {
  name: "App",
  data() {
    return {
      tela: "inicio",
      etapa: "palavra",
      palavra: "",
      dica: "",
      erros: 0,
      letras: [],
    };
  },
  components: {
    FormularioJogo,
    InicioJogo,
  },
  methods: {
    setPalavra: function (palavra) {
      this.palavra = palavra;
      this.etapa = "dica";
    },
    setDica: function (dica) {
      this.dica = dica;
      this.tela = "jogo";
      this.etapa = "jogo";
    },
    verificarLetra: function (letra) {
      return this.letras.find(
        (item) => item.toLowerCase() === letra.toLowerCase()
      );
    },
    jogar: function (letra) {
      // Adiciona letra jogada
      this.letras.push(letra);

      // Validar Erro
      this.verificarErros(letra);
    },
    verificarErros: function (letra) {
      // Acerto
      if (this.palavra.toLowerCase().indexOf(letra.toLowerCase()) >= 0) {
        return this.verificarAcertos();
      }
      //Erros
      this.erros++;

      //Enforcado
      if (this.erros === 6) {
        this.etapa = "enforcado";
      }
    },
    verificarAcertos: function () {
      let letrasUnicas = [...new Set(this.palavra.split(""))];
      if (letrasUnicas.length === this.letras.length - this.erros) {
        this.etapa = "ganhador";
      }
    },
    jogarNovamente: function () {
      this.palavra = "";
      this.dica = "";
      this.erros = 0;
      this.letras = [];
      this.tela = "inicio";
      this.etapa = "palavra";
    },
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
