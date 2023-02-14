<script setup>
import Tictactoe from './components/Tictactoe.vue'
import ShoppingList from './components/ShoppingList.vue'
import { ref } from 'vue';
const changePage = ref(0)







</script>






<template>
  <div class="navbar">
    <button @click="changePage = 0">TicTacToe</button>
    <button @click="changePage = 1">Shopping List</button>
  </div>
  <div v-if="changePage === 0"> 
    <Tictactoe />
  </div>
  <div v-if="changePage === 1">
    <ShoppingList/>
  </div>
</template>

<style scoped>

.navbar{
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  margin-top: 1rem;
}


</style>
