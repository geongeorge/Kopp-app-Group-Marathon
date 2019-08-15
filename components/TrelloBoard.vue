<template>
  <div class="mt-3">
    <!-- <div class="embed-container">
      <iframe :src="'https://trello.com/b/'+bData.player.id+'.html'"  id="iHateRegex" frameborder="0"></iframe>
    </div> -->
    <h2 class="text-gray-600">{{bData.player.name}}</h2>
    <div class="bg-gray-300 rounded mt-1 shadow-inner flex mx-auto w-auto scrolling-touch overflow-x-scroll">
        <div class="flex-none w-64 m-2" v-for="(tlist, key) in bData.lists" :key="key">
         <TrelloList :tlist="tlist"></TrelloList>
        </div>
    </div>
  </div>
</template>

<script>
import TrelloList from './TrelloList'
export default {
components:{
    TrelloList
},
  props: {
    bData :{default: {}}
    // bData.player -> name,id
    // bData.lists -> [ { id, name}, ... ]
  },
  data() {
    return {
      
    };
  },
  mounted() {
      console.log(this.bData)
  }
};
</script>

<style>
.embed-container {
  position: relative;
  height: auto;
  overflow: hidden;
  max-width: 100%;
}
.embed-container iframe,
.embed-container object,
.embed-container embed {
  top: 0;
  left: 0;
  width: 100%;
}
</style>