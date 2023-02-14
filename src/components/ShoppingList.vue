<script>
export default {
  data() {
    return {
      message: "I'm a Shopping List",
      list: []
    }

  },
  methods: {
    addTolist(submitEvent) {
       this.list.push(submitEvent.target[0].value)
    }
  }
}



</script>

<template>
    <h1>{{message}}</h1>
    <form action="" @submit.prevent="addTolist">
        <input
      v-model="text">
        <button type="submit">Add Item To List</button>
    </form>
    <p v-for="item in list">{{ item }}</p>

</template>

<style>
</style>