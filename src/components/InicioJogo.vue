<template>
  <div class="jogo">
    <CorpoForca :erros="erros" />

    <PalavraJogo
      :palavra="palavra"
      :dica="dica"
      :verificarLetra="verificarLetra"
      :etapa="etapa"
    />

    <TecladoJogo
      v-if="etapa === 'jogo'"
      :letras="letras"
      :verificarLetra="verificarLetra"
      :jogar="jogar"
    />

    <FimJogo
      v-if="etapa != 'jogo'"
      :etapa="etapa"
      :texto="etapa === 'ganhador' ? 'Acertou :)' : 'Errou, fim de jogo :('"
      :jogarNovamente="jogarNovamente"
    />
  </div>
</template>

<script>
import CorpoForca from "./CorpoForca.vue";
import PalavraJogo from "./PalavraJogo.vue";
import TecladoJogo from "./TecladoJogo.vue";
import FimJogo from "./FimJogo.vue";

export default {
  name: "InicioJogo",
  props: {
    erros: Number,
    palavra: String,
    dica: String,
    verificarLetra: Function,
    etapa: String,
    letras: Array,
    jogar: Function,
    jogarNovamente: Function,
  },
  data() {
    return {};
  },
  methods: {},
  components: {
    CorpoForca,
    PalavraJogo,
    TecladoJogo,
    FimJogo,
  },
};
</script>

<style>
.jogo {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}
</style>