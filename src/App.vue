<template>
  <h1>Bulletin board</h1>

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
      <h3>Detail</h3>
      <p>{{ modalInfo }}</p>
      <button @click="closeModal()">close</button>
    </div>
  </div>

</template>

<script>
  export default {
    name: 'App',
    data() {
      return {
        colors: ["red", "blue", "green", "yellow", "purple", "orange", "pink", "brown", "black", "white"],
        isModal: false,
        modalInfo: '',
        data: [
          {
            title: 'Title 1',
            regist_time: '2025-03-24 02:07',
            tag: ['Information', 'Top 10'],
            content: 'This is Title 1',
            like: 0
          },
          {
            title: 'Title 2',
            regist_time: '2025-03-24 02:15',
            tag: ['Information', 'Humor'],
            content: 'This is Title 2',
            like: 0
          },
          {
            title: 'Title 3',
            regist_time: '2025-03-24 02:15',
            tag: ['CS', 'Humor'],
            content: 'This is Title 3',
            like: 0
          },
          {
            title: 'Title 4',
            regist_time: '2025-03-24 02:07',
            tag: ['Information', 'Top 10'],
            content: 'This is Title 4',
            like: 0
          },
          {
            title: 'Title 5',
            regist_time: '2025-03-24 02:15',
            tag: ['Information', 'Humor'],
            content: 'This is Title 5',
            like: 0
          },
          {
            title: 'Title 6',
            regist_time: '2025-03-24 02:15',
            tag: ['CS', 'Humor'],
            content: 'This is Title 6',
            like: 0
          },
          {
            title: 'Title 7',
            regist_time: '2025-03-24 02:15',
            tag: ['CS', 'Humor'],
            content: 'This is Title 7',
            like: 0
          },
          {
            title: 'Title 8',
            regist_time: '2025-03-24 02:07',
            tag: ['Information', 'Top 10'],
            content: 'This is Title 8',
            like: 0
          },
          {
            title: 'Title 9',
            regist_time: '2025-03-24 02:15',
            tag: ['Information', 'Humor'],
            content: 'This is Title 9',
            like: 0
          },
          {
            title: 'Title 10',
            regist_time: '2025-03-24 02:15',
            tag: ['CS', 'Humor'],
            content: 'This is Title 10',
            like: 0
          },
          {
            title: 'Title 11',
            regist_time: '2025-03-24 02:15',
            tag: ['CS', 'CV'],
            content: 'This is Title 11',
            like: 0
          }
        ]
      }
    },
    methods: {
      openModal(item) {
        this.isModal = true;
        this.modalInfo = item.content
      },
      closeModal() {
        this.isModal = false;
      }
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
