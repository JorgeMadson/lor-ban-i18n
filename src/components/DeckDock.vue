<template>
  <div class="dock">
    <label for="deck-code">Cole seu código:</label>
    <input id="deck-code" v-model="code" placeholder="CEBAIAIFB4WDANQIAEAQGDAUDAQSIJZUAIAQCBIFAEAQCBAA">
    <ul id="array-rendering" v-if="!error">
      <li  v-for="card in decodedDeck" :key="card.code">
        {{card.count}}x {{card.code}}
      </li>
    </ul>
    <p v-else> {{error}} </p>
    
  </div>
</template>
  
<script>
import { DeckEncoder } from 'runeterra';

  export default {
  name: 'DeckDock',
  data() {
    return { code: '', decodedDeck: '', error: ''};
  },
  watch: {
      // Se o código tiver mais de 30 caracteres ele faz a request
      code(novoCode) { //oldQuestion
        if (novoCode.length > 30) {
          this.decodeCode(novoCode);
        }
      }
    },
  methods: {
    decodeCode(code) {
      try{
        let decodedDeck = DeckEncoder.decode(code);
        this.decodedDeck = decodedDeck;
        this.error = '';
      }
      catch(e){
        this.error = 'Código inválido!';
        console.error(e);
      }
    }
  }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .dock {
    /* .bg-dark-mode { */
    background-color: #1e1e2f
    }
</style>
  