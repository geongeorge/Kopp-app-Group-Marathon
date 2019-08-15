<template>
  <div class="container mycontainer mx-auto p-4">
    <h1 class="text-center text-5xl font-light text-gray-800">
      <span class="text-red-600 font-bold">Kopp</span>.app
    </h1>
  <div class="border-gray-300 border p-3 rounded">
    <h2 class="text-gray-800 text-3xl">Players</h2>
    <div class="flex flex-wrap justify-start">
      <div class="m-1 px-2 text-white bg-purple-500 border-purple-600 border rounded hover:underline" v-for="(pl,key) in users" :key="key"><h2><a :href="'https://trello.com/b/'+pl.id" target="_blank">{{pl.name}}</a></h2>
      </div>
    </div>
  </div>
  <div>
    <TrelloBoard v-for="(bData,key) in boardData" :bData="bData" :key="key"></TrelloBoard>
  </div>
    
  </div>
</template>

<script>
import TrelloBoard from "~/components/TrelloBoard.vue";
import players from '~/static/players.json'

import axios from 'axios'   

export default {
  components: {
    TrelloBoard
  },
  data() {
    return {
      users: players
    };
  },
  mounted() {
    console.log(this.boardData)
  },
  async asyncData({ params }) {
    let boardData = [];
    for (const player of players) {
      
      let apiUrl = `https://api.trello.com/1/boards/${player.id}/lists`;
      let result = await axios.get(apiUrl)
      boardData.push({
        player: player,
        lists: result.data
      })
      
    }
    return {
      boardData: boardData
    };
  },
  head () {
    return {
      title: "The Kopp App",
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        { hid: 'description', name: 'description', 
        content: 'Progress togather...' }
      ]
    }
  }
};
</script>

<style>
h1,
h2,
h3 {
  font-family: "Rubik", sans-serif;
}
.mycontainer {
  max-width: 850px;
}
</style>
