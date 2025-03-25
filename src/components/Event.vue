<template>
    <div class="event" :class="{show: isOpen}">
        <p>{{ text }}</p>
        <button @click="isOpen=false">X</button>
    </div>
</template>
<script>
export default {
    name: "EventComponent",
    props: {
        text: String,
        isEventOpen: Boolean
    },
    data() {
        return {
            isOpen: true
        }
    }
}
</script>
<style>
    .event {
        background: #444;
        color: #fff;
        padding: 10px 20px;
        text-align: center;
        font-size: small;
        display: flex;
        justify-content: space-between;
        align-items: center;
        display: none;
    }
    .event p {
        flex-grow: 1;
        /* text-align: center; */
        margin: 0;
    }

    .show {
        display: flex;
    }

    .event button {
        margin: 0;
    }
</style>