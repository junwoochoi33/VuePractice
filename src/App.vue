<template>
  <h1>Bulletin board</h1>

  <div v-for="(item, i) in data" :key="i">
    <h3 class="bg-gold pad-title" :style="item.title_text_color">{{ item.title }}</h3>
    <p>Registed datetime: {{ item.regist_time }}</p>
    <p>Tags: {{ item.tag.join(', ') }}</p> 
    <button @:click="item.like++"><span>Like: {{ item.like }}</span></button>
  </div>

</template>

<script>
  export default {
    name: 'App',
    data() {
      return {
        data: [
          {
            title: 'Title 1',
            title_text_color: "color: white",
            regist_time: '2025-03-24 02:07',
            tag: ['Information', 'Top 10'],
            like: 0
          },
          {
            title: 'Title 2',
            title_text_color: "color: black",
            regist_time: '2025-03-24 02:15',
            tag: ['Information', 'Humor'],
            like: 0
          },
          {
            title: 'Title 3',
            title_text_color: "color: purple",
            regist_time: '2025-03-24 02:15',
            tag: ['CS', 'Humor'],
            like: 0
          }
        ]
      }
    }
  }
</script>

<style>
  .bg-gold {
    background: gold;
  }
  .pad-title {
    padding: 10px;
  }
</style>
