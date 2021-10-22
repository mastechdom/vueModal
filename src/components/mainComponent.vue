<template>
    <h1>Hi Azhar </h1>
    <button class="btn btn-primary" @click="openModal">
        Make An Offer
    </button>
    <div class="container modalContainer" v-if="show">
        <div class="row">
            <div class=""></div>
        </div>
        <Modal v-on:close-modal="closeModal()" />
    </div>
</template>

<script>
import Modal from './modal.vue'

export default{
    components: {
        Modal,
    },
    data() {
        return {
            show: false
        };
    },
    methods: {
        openModal() {
            this.show = true;
        },
        closeModal() {
            this.show = false;
        }
    }
}
</script>


<style scoped>
/* .btn {
    height: 50px;
    width: 10%;
    background: yellow;
    border-radius: 5px;
} */

</style>