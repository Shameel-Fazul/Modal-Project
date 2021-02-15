<template>
  <h1>{{ title }}</h1>
  <input type="text" ref="name">
  <button @click="handleClick">click me</button>
  <Modal />
</template>

<script>
import Modal from './components/Modal'

export default {
  name: 'App',
  components: { Modal },
  data() {  // Component Object
    return {
      title: 'Shameel Fazul'
    }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name) // referencing DOM elements. Template Refs; like queryselector
      this.$refs.name.classList.add('active') //adding the class 'active' to the input element
       this.$refs.name.focus()
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
