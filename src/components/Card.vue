<template>
<li class="card">
    <h2>{{card.count}}x</h2>
    <img :src="cardUrl(card.code)" style="width:10rem">
    
</li>
</template>
  
<script>
    export default {
        name: 'Card',
        data: function() {
            return {
                deck: 'deck'
            }
        },
        props: ['card'],
        methods: {
            cardUrl(cardCode) {
                let set = cardCode.slice(1,2)
                return `https://cdn-lor.mobalytics.gg/production/images/set${set}/pt_br/img/card/game/${cardCode}.webp`
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card {
    padding: 0 0 2rem 2rem;
}
</style>
  