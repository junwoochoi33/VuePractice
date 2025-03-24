<template>
<Navbar />

  <h1>Bulletin Board</h1>

  <div class="item" v-for="(item, i) in data" :key="i">
    <figure>
      <img src="https://picsum.photos/200/200" :alt="item.title">
    </figure>
    <div class="info">
      <h3 class="bg-gold pad-title" :style="'color: '+colors[Math.floor(i%10)]">{{ item.title }}</h3>
      <p>Registed datetime: {{ item.regist_time }}</p>
      <p>Tags: {{ item.tag.join(', ') }}</p> 
      <button @:click="item.like++"><span>Like: {{ item.like }}</span></button>
    </div>
    <p>
      <button @click="openModal(item)">show detail</button>
    </p>
  </div>

  <div class="modal" v-if="isModal">
    <div class="inner">
      <h3>{{ selectedItem.title }}</h3>
      <p>{{ selectedItem.content }}</p>
      <button @click="closeModal()">close</button>
    </div>
  </div>

</template>

<script>
  import { colors } from './assets/colors';
  import { data } from './assets/data/board';
  import Navbar from './components/Navbar.vue';

  export default {
    name: 'App',
    data() {
      return {
        colors: colors,
        isModal: false,
        selectedItem: null,
        data: data
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
      Navbar: Navbar
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


  h1, h2, h3 {
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

  .modal {
    background: rgba(0, 0, 0, 0.7);
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .modal .inner {
    background: #fff;
    width: 80%;
    padding: 20px;
    border-radius: 10px;
  }

</style>
