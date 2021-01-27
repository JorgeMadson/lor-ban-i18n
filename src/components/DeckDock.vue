<template>
  <div class="dock">
    <label for="deck-code">Cole seu código:</label>
    <input
      id="deck-code"
      v-model="code"
      placeholder="CEBAIAIFB4WDANQIAEAQGDAUDAQSIJZUAIAQCBIFAEAQCBAA"
    />
    <template id="array-rendering" v-if="!error">
      <ul class="card" v-if="!error">
        <card
          v-for="decodeCard in decodedDeck"
          :card="decodeCard"
          :key="decodeCard.code"
        >
        </card>
      </ul>
    </template>
    <p v-else>{{ error }}</p>
  </div>
</template>
  
<script>
import { DeckEncoder } from "runeterra";
import Card from "../components/Card.vue";

export default {
  components: { Card },
  name: "DeckDock",
  data() {
    return { code: "", decodedDeck: "", error: "" };
  },
  created() {
    let urlParams = new URLSearchParams(window.location.search);
    this.code = urlParams.has("code") ? urlParams.get("code") : '';
  },
  watch: {
    // Se o código tiver mais de 30 caracteres ele faz a request
    code(novoCode) {
      //oldQuestion
      if (novoCode.length > 30) {
        this.decodeCode(novoCode);
      }
    },
  },
  methods: {
    decodeCode(code) {
      try {
        let decodedDeck = DeckEncoder.decode(code);
        this.decodedDeck = decodedDeck;
        this.error = "";
      } catch (e) {
        this.error = "Código inválido!";
        console.error(e);
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.dock {
  /* .bg-dark-mode { */
  background-color: #1e1e2f;
}
.card {
  display: flex;
  flex-flow: wrap;
}
</style>
  