<template>
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
</template>
<script>
import colors from '../assets/colors';

export default {
    name: 'ItemComponent',
    data() {
        return {
            colors: colors
        }
    },
    props: {
        data: Array,
    },
    mounted() {
        console.log("Items.vue data:", this.data);
    },
    methods: {
        openModal(item) {
            this.$emit('openModal', item);
        }
    }
}
</script>
<style>
    .container {
        padding: 20px;
    }
</style>