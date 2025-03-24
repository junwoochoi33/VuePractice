<template>
    <div class="modal" v-if="isModal">
        <div class="inner">
            <h3>{{ selectedItem.title }}</h3>
            <p>{{ selectedItem.content }}</p>
            <button @click="closeModal()">close</button>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'ModalComponent'
    }
</script>

<style>
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