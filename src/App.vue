<template>
  <div>
    <h1>{{ title }}</h1>
    <p>Welcome</p>

    <teleport to=".modals" v-if="showModal">
      <Modal theme="sale" @close="toggleModal">
        <template v-slot:links>
          <a href="#">Sign up now</a>
          <a href="#">More info</a>
        </template>
        <h1>Sign up for The Giveaway!</h1>
        <p>Some random text</p>
        <template v-slot:secondModal v-if="showModalTwo">
          <h1>Sign up for The Secondmodal!</h1>
          <p>Some other random text</p>
        </template>
      </Modal>
    </teleport>

    <teleport to=".modals" v-if="showModalTwo">
      <Modal @close="toggleModalTwo">
        <h1>Sign up for the newsletter!</h1>
        <p>For updates and promo codes</p>
      </Modal>
    </teleport>
    <button @click.alt="toggleModal">Open modal</button>
    <button @click="toggleModalTwo">Open second modal</button>
  </div>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  data() {
    return {
      title: "My first title",
      showModal: false,
      showModalTwo: false,
    };
  },
  components: {
    Modal,
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    },
  },
};
</script>

<style>
#app,
.modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
