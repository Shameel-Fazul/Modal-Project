<template>
  <h1>{{ title }}</h1>
  <br>
  <input type="text" ref="name">
  <button @click="handleClick">click me</button>
  <teleport to=".modals" v-if="showModal"> <!-- Teleports this to anywhere in the DOM; ex: to the div with the .modals class in index -->
    <Modal :header="header" text="Grab your ninja swag for half price" theme="sale" @close="toggleModal"> <!-- Sending props to other components - single source of truth (SSOT) --> <!-- Use data binding to add dynamic values or arrays; ex: header -->
     <template v-slot:links> <!-- Slot directive to assign a custom slot name -->
       <a href="#">Sign up now</a> <!-- Named slots to organize the template in the child component -->
       <a href="#">more info</a>
     </template>
     <h1>Slot Example</h1>  <!-- default slot -->
     <p>Slots are similar to props, but it's used to send templates to child components</p>
    </Modal>
  </teleport>
  <br>
  <button @click.alt="toggleModal">toggle modal (event modifier [alt])</button>
  <br>
  <p>Cookie Modal</p>
  <div v-if="showCookieModal">
    <Modal :header="cookieTitle" :text="CookieContent" @close="toggleCookieModal">
      <template v-slot:links>
        <a href="#" @click="toggleCookieModal">Agree</a>
         <a href="#" @click="toggleCookieModal">Disagree</a>
      </template>
      <p>According to internet privacy laws, we need your permission before storing data for better user experience</p>
    </Modal>
  </div>
  <button @click="toggleCookieModal">toggle cookie modal</button>
</template>

<script>
import Modal from './components/Modal'

export default {
  name: 'App',
  components: { Modal },
  data() {  // Component Object
    return {
      title: 'Shameel Fazul',
      header: "Sign up for the giveaway",
      showModal: false,
      cookieTitle: 'Privacy',
      cookieContent: 'This site stores data in your device',
      showCookieModal: false
    }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name) // referencing DOM elements. Template Refs; like queryselector
      this.$refs.name.classList.add('active') //adding the class 'active' to the input element
       this.$refs.name.focus()
    },
    toggleModal() {
      this.showModal = !this.showModal
    },
     toggleCookieModal() {
      this.showCookieModal = !this.showCookieModal
    }
  }
}
</script>

<style> /** <style scoped> to only apply styles to this component */
#app, .modals {
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
