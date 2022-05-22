<template>
    <button class="btn" @click="setLock" v-bind:class="{ onclick: isClick }">
        <slot></slot>
    </button>
</template>

<script>
export default {
    props: {

    },
    data() {
        return {
            isClick: false,
        }
    },
    methods: {
        setLock() {
            if (!this.isClick) {
                this.isClick = true;
            } else {
                this.isClick = false;
            }
        }
    }
}

</script>

<style scoped>
.btn {
    width: 20%;
    height: 70%;
    background-color: blue;
    margin: auto;
}

.onclick {
    width: 30%;
    height: 90%;
    background-color: red;
}
</style>