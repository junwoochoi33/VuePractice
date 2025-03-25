<template>
    <div class="container">
    <h1>Countries</h1>
    <div class="item" v-for="(country, code) in countries" :key="code">
      <figure>
        <img :src="require(`@/assets/image/flag/${code.toLowerCase()}.svg`)" :alt="country">
      </figure>
      <div class="info">
        <h3>{{ country }}</h3>
      </div>
      <p>
        <button @click="openModal(code)">show detail</button>
      </p>
    </div>
  </div>
</template>
<script>
import countries from '@/assets/data/countries';

export default {
    name: 'ItemComponent',
    data() {
        return {
            countries: countries
        }
    },
    props: {
        
    },
    mounted() {
        console.log(countries);
    },
    methods: {
        openModal(code) {
            this.$emit('openModal', code);
        }
    }
}
</script>
<style>
    .container {
        padding: 20px;
    }
</style>