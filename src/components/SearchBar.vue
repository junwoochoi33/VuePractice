<template >
    <div class="search-box">
        <input type="search" 
        v-model="inputText"
        placeholder="input search keyword...">
        <button>search</button>
    </div>
    <p>{{ inputText }}</p>
</template>
<script>
export default {
    name: 'SearchBarComponent',
    data() {
        return {
            inputText: ''
        }
    },
    watch: {
        
    }  
        
    
}
</script>
<style >
    
</style>