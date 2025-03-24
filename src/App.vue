<template>

  <Navbar />
  <Event :text="event_text" />
  
  

  <div class="container">
    <h1>Bulletin Board</h1>
    <div class="item" v-for="(item, i) in data" :key="i">
      <figure>
        <img src="https://picsum.photos/200/200" :alt="item.title">
      </figure>
      <div class="info">
        <h3 class="bg-gold pad-title" :style="'color: ' + colors[Math.floor(i % 10)]">{{ item.title }}</h3>
        <p>Registed datetime: {{ item.regist_time }}</p>
        <p>Tags: {{ item.tag.join(', ') }}</p>
        <button @click="item.like++"><span>Like: {{ item.like }}</span></button>
      </div>
      <p>
        <button @click="openModal(item)">show detail</button>
      </p>
    </div>
  </div>

  <Modal :isModal="isModal" :selectedItem="selectedItem" @closeModal="closeModal"/>

</template>

<script>
import colors from './assets/colors';
import data from './assets/data/board';
import Navbar from './components/Navbar' 
import Modal from './components/Modal';
import Event from './components/Event';


export default {
  name: 'App',
  data() {
    return {
      colors: colors,
      isModal: false,
      selectedItem: null,
      data: data,
      event_text: 'Welcome to Bulletin Board!'
    }
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
