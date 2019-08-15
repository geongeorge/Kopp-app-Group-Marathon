<template>
<div class="min-h-full">
    <div>
        <h2>{{tlist.name}} ({{cardsCount}})</h2>
    </div>
  <div class="h-48 rounded shadow-inner p-1 overflow-y-scroll bg-gray-400">
      <TrelloCard v-for="(card,key) in cards" :key="key" :url="card.shortUrl">{{card.name}}</TrelloCard>
      <div v-if="cards.length<=0 && loaded" class="text-center">
          <span class="text-gray-600">yes, im lazy</span>
      </div>
  </div>
  </div>
</template>

<script>
import TrelloCard from './TrelloCard'
export default {
    components:{
        TrelloCard
    },
    data() {
        return {
            cards: [],
            loaded: false
        }
    },
    props: {
        tlist : {default: {}}
    },
    mounted() {
        console.log(this.tlist.id)
        this.fetchcards()
    },
    methods: {
        async fetchcards() {
            let apiUrl = `https://api.trello.com/1/lists/${this.tlist.id}/cards`
            const cards = await this.$axios.$get(apiUrl)
            this.cards = cards
            this.loaded = true
        }
    },
    computed: {
        cardsCount(){
            return this.cards.length;
        }
    }
}
</script>

<style>

</style>