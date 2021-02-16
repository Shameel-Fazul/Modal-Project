<template>
  <h1>{{ title }}</h1>
  <input type="text" ref="name">
  <button @click="handleClick">click me</button>
  <Modal :header="header" text="Grab your ninja swag for half price" theme="sale" /> <!-- Sending props to other components - single source of truth (SSOT) --> <!-- Use data binding to add dynamic values or arrays; ex: header -->
</template>

<script>
import Modal from './components/Modal'

export default {
  name: 'App',
  components: { Modal },
  data() {  // Component Object
    return {
      title: 'Shameel Fazul',
      header: "Sign up for the giveaway"
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

<style> /** <style scoped> to only apply styles to this component */
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
