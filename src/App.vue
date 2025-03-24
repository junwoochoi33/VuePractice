<template>
  <h1>게시판</h1>

  <div v-for="(item, i) in data" :key="i">
    <h3 class="bg-gold pad-title" :style="item.title_text_color">{{ item.title }}</h3>
    <p>등록일시: {{ item.regist_time }}</p>
    <p>태그: {{ item.tag.join(', ') }}</p> 
  </div>

</template>

<script>
  export default {
    name: 'App',
    data() {
      return {
        data: [
          {
            title: '제목 1',
            title_text_color: "color: white",
            regist_time: '2025-03-24 02:07',
            tag: ['정보', '인기'],
          },
          {
            title: '제목 2',
            title_text_color: "color: black",
            regist_time: '2025-03-24 02:15',
            tag: ['정보', '유머'],
          },
          {
            title: '제목 3',
            title_text_color: "color: purple",
            regist_time: '2025-03-24 02:15',
            tag: ['심리', '유머'],
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
