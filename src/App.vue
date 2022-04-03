<template>
  <h1>{{ title }}</h1>
  <p>click to open</p>

  <teleport to="#modals" v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
     
      <template v-slot:links>
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
      <h1>Thanks for clicking</h1>
      <p>You can now exit by clicking outside the box</p>
    </Modal>
  </teleport>  

  <teleport to="#modals" v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <h1>Thanks for clicking</h1>
      <p>You can now exit by clicking outside the box</p>
    </Modal>
  </teleport>

  <button @click.alt="toggleModal">modal 1 (alt click)</button>
  <button @click="toggleModalTwo">modal 2</button>
</template>

<script>
import Modal from './components/Modal'

export default {
  name: 'App',
  components: { Modal },
  data() {
    return {
      title: 'My First Vue App!',
      showModal: false,
      showModalTwo: false,
    }
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    }
  }
}
</script>

<style>
#app, #modals {
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
button {
  background: #bbb;
  padding: 10px;
  border: none;
  border-radius: 4px;
  margin: 10px;
  font-size: 16px;
  color: #333;
}
</style>