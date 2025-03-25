<template>

  <Navbar />
  <Event :text="event_text" />
  
  <Items :data="data" @openModal="openModal" />

  <Modal :isModal="isModal" :selectedItem="selectedItem" @closeModal="closeModal"/>

</template>

<script>
import data from './assets/data/board';
import Navbar from './components/Navbar' 
import Modal from './components/Modal';
import Event from './components/Event';
import Items from './components/Items.vue'


export default {
  name: 'App',
  data() {
    return {
      isModal: false,
      selectedItem: null,
      data: data,
      event_text: 'Welcome to Bulletin Board!'
    }
  },
  mounted() {
    console.log("App.vue data:", this.data);
  },
  methods: {
    openModal(item) {
      this.isModal = true;
      this.selectedItem = item
      },
    closeModal() {
      this.isModal = false;
    }
  },
  components: {
    Navbar: Navbar,
    Modal: Modal,
    Event: Event,
    Items: Items 
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
}

body {
  max-width: 768px;
  margin: 0 auto;
  padding: 20px
}


h1,
h2,
h3 {
  margin-bottom: 1rem;
}

p {
  margin-bottom: 0.5rem;
}

button {
  margin-right: 10px;
  margin-top: 1rem;
}

.item {
  width: 100%;
  border: 1px solid #ccc;
  display: flex;
  margin-bottom: 20px;
  padding: 1rem;
}

.item figure {
  width: 30%;
  margin-right: 1rem;
}

.item img {
  width: 100%;
}

.item .info {
  width: 100%;
}
</style>
