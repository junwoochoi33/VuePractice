<template>

  <Navbar />
  <Event :text="event_text" />

  <SearchBar />
  
  <Countries @openModal="openModal" />

  <Modal :isModal="isModal" :selected="selected" @closeModal="closeModal"/>

</template>

<script>
import Navbar from './components/Navbar' 
import Modal from './components/Modal';
import Event from './components/Event';
import SearchBar from './components/SearchBar.vue'
import Countries from './components/Countries.vue';


export default {
  name: 'App',
  data() {
    return {
      isModal: false,
      selected: null,
      event_text: 'Welcome to Countries!'
    }
  },
  mounted() {
    
  },
  methods: {
    openModal(code) {
      this.isModal = true;
      this.selected = code
      },
    closeModal() {
      this.isModal = false;
    }
  },
  components: {
    Navbar: Navbar,
    Modal: Modal,
    Event: Event,
    SearchBar: SearchBar,
    Countries: Countries,
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
