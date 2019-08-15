<template>
  <div class="container mx-auto p-4">
    <h1 class="text-center text-5xl font-light text-gray-800"><span class="text-red-600 font-bold">No</span>Bullshit</h1>

    <TrelloBoard :tid="userid"></TrelloBoard>

    <div class="shadow">Hello</div>
  </div>
</template>

<script>
import TrelloBoard from '~/components/TrelloBoard.vue'

export default {
  components: {
    TrelloBoard
  },
  data() {
    return {
      users: [
        {
          name: "Geon",
          id: "vtuWFs7X"
        },
        {
          name: "jithin",
          id: "vtuWFs7X"
        },
      ]
    }
  }
}
</script>

<style>
h1,h2,h3 {
  font-family: 'Rubik', sans-serif;
}
</style>
