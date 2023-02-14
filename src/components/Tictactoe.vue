<script setup>
import { ref } from "vue";

defineProps({
});
const board = ref(["","","","","","","","",""])
const player = ref(null)

const winner = ref(false)

const winCondition = [
	[0, 1, 2],
	[3, 4, 5],
	[6, 7, 8],
	[0, 3, 6],
	[1, 4, 7],
	[2, 5, 8],
	[0, 4, 8],
	[2, 4, 6]
]


function pickPlayer(e){
if(this.winner === false) {
  if(e.textContent === "Play as X"){
    this.player = "X"
  } else{
    this.player = "O"
  }
}

}


function getField(e, index) {
  console.log(this.player)
  console.log(e)
  if(this.player === "X" && e.textContent === "-"){
    e.textContent="X"
    this.board[index] = "X"
    CheckWin(this.player, this.winCondition)
    if(this.winner === false){
      this.player = "O"
    }
  } else if (this.player === "O" && e.textContent === "-"){
    e.textContent="O"
    this.board[index] = "O"
    CheckWin(this.player, this.winCondition)
    if(this.winner === false) {
      this.player = "X"
    }
  } 
}  

function CheckWin(player, winCondition) {

  //ForEach for vær Array inde i winCondition Array'en
  winCondition.forEach((condition) => {
    // her tjekker vi om feks. 3 X på strippe findes på brættet. Man kan google "JS tiktaktoe win condition" for en bedere forklaring
    if (
      board._rawValue[condition[0]] === player &&
      (board._rawValue[condition[1]] === player) & (board._rawValue[condition[2]] === player)
    ) {
      winner._value = true

    }
  });
}



</script>

<template>
  <div class="buttons">
    <button @click="pickPlayer($event.target)">Play as X</button>
    <button @click="pickPlayer($event.target)">Play as O</button>
  </div>
  <h1 v-if="winner">The Winner is {{ player }}</h1>
  <div class="grid">
    <p v-for="(nr, index) in board" @click="getField($event.target, index)">-</p>
  </div>

</template>

<style scoped>
.read-the-docs {
  color: #888;
}

.buttons{
  display: flex;
  gap:1rem;
  justify-content: center;
  margin-bottom: 1rem
  ;
}
.grid{
  width: 500px;
  height: 500px;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  border: 1px solid red;  
  
}
.grid p{
  border: 1px solid red;
  height: 100%;
  width: 100%;
  font-size: 32px;
  margin: 0;
  display: flex;
  align-items: center;
  justify-content: center;

}
</style>
