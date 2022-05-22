<template>
    <div class="lib">
        <button class="btn" @click="setLock('0')" v-bind:class="{ onclick: but[0] }">
            11
        </button>
        <button class="btn" @click="setLock('1')" v-bind:class="{ onclick: but[1] }">
            22
        </button>
        <button class="btn" @click="setLock('2')" v-bind:class="{ onclick: but[2] }">
            33
        </button>
         <button class="btn" @click="setLock('3')" v-bind:class="{ onclick: but[3] }">
            44
        </button>
         <button class="btn" @click="setLock('4')" v-bind:class="{ onclick: but[4] }">
            55
        </button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            but: {
                active1: false,
                active2: false,
                active3: false,
                active4: false,
                active5: false,
            },

            isClick: false,
        }
    },
    methods: {
        setLock(n) {
            if (!this.but[n]) {
                this.closeAll();
                this.but[n] = true;
            } else {
                this.closeAll();
                this.but[n] = false;
            }
        },

        closeAll() {
            this.but[0] = false;
            this.but[1] = false;
            this.but[2] = false;
            this.but[3] = false;
            this.but[4] = false;
        }
    }
}
</script>

<style scoped>
.lib {
    width: 50%;
    height: 100px;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: auto;
}

.btn {
    width: 15%;
    height: 40%;
    /* background-color: blue; */
    margin: auto;
}

.onclick {
    width: 20%;
    height: 60%;
    /* background-color: red; */
}
</style>