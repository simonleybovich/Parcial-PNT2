<template>
  <section class="src-components-formulario">
    <form>
      <input type="text" id="texto" v-model.trim="texto" />
      <h5>Cantidad caracteres = {{ contador }}</h5>
    </form>
    <ol>
      <li>{{ codificado }} (codificado)</li>
      <li>{{ mayuscula }} (mayuscula)</li>
      <li>{{ minuscula }} (minuscula)</li>
      <li>{{ mayusMinus(this.texto) }} (mayuscula / minuscula)</li>
      <li>{{ minusMayus(this.texto) }} (minuscula / mayuscula)</li>
    </ol>
  </section>
</template>

<script>
export default {
  name: "src-components-formulario",
  props: [],
  mounted() {},
  data() {
    return {
      texto: "",
    };
  },
  methods: {
    mayusMinus(texto) {
      let text = "";
      for (let i = 0; i < texto.length; i++) {
        if (i % 2 === 0) {
          text += texto[i].toUpperCase();
        } else {
          text += texto[i].toLowerCase();
        }
      }
      return text;
    },
    minusMayus(texto) {
      let text = "";
      for (let i = 0; i < texto.length; i++) {
        if (i % 2 === 0) {
          text += texto[i].toLowerCase();
        } else {
          text += texto[i].toUpperCase();
        }
      }
      return text;
    },
  },
  computed: {
    codificado() {
      const texto = this.texto.toLocaleLowerCase();
      return texto.replace(/[aeiouAEIOU]/g, function (char) {
        switch (char) {
          case "a":
            return "u";
          case "e":
            return "o";
          case "o":
            return "e";
          case "u":
            return "a";
          default:
            return char;
        }
      });
    },
    minuscula() {
      return this.texto.toLowerCase();
    },
    mayuscula() {
      return this.texto.toUpperCase();
    },
    contador() {
      return this.texto.length;
    },
  },
};
</script>
<style scoped lang="css"></style>
