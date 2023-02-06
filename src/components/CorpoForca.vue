<template>
  <div class="forca">
    <img 
      :src="`https://raw.githubusercontent.com/rodrisoares/jogoForcaVue/main/src/assets/${erros}.svg`"
      alt="Imagem de uma forca"
    />
  </div>
</template>

<script>
export default {
  name: "CorpoForca",
  props: {
    erros: Number,
  },
  data() {
    return {};
  },
  methods: {},
};
</script>

<style>
.forca img {
  height: 250px;
}
</style>