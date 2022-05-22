<template>
    <div class="lib">
        <div class="btns">

            <button class="btn" @click="setLock('0')" v-bind:class="{ onclick: but[0] }">
                Земля
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

        <div class="item" v-show="this.but[0]">

            <div class="head">
                <div class="audioblock">
                    <h3>Земля</h3>
                    <audio style="color: red" :src='Items.audio' controls></audio>
                </div>
                <img :src='Items.img' alt="">
            </div>

            <div class="info">
                <div class="text">
                    <h4>
                        Земля́ — третья по удалённости от Солнца планета Солнечной системы. Самая плотная, пятая по
                        диаметру
                        и массе среди всех планет и крупнейшая среди планет земной группы, в которую входят также
                        Меркурий,
                        Венера и Марс. Единственное известное человеку в настоящее время тело во Вселенной, населённое
                        живыми организмами.
                    </h4>

                    <a :href='Items.wiki' target="_blank">ЗЕМЛЯ на Вики</a>
                </div>
            </div>

        </div>

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

            Items: {
                img: "https://upload.wikimedia.org/wikipedia/commons/thumb/0/0d/Africa_and_Europe_from_a_Million_Miles_Away.png/1024px-Africa_and_Europe_from_a_Million_Miles_Away.png",
                audio: "http://drive.google.com/uc?export=view&id=1qoRFm_c0m7oRVFMGsoAIm2UHHY5JkOPP",
                wiki: "https://ru.wikipedia.org/wiki/%D0%97%D0%B5%D0%BC%D0%BB%D1%8F",
            },


            isClick: false,

            aItem: false,
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
    height: auto;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: auto;

    flex-direction: column;
}

.btns {
    width: 100%;
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

.head {
    display: flex;
    flex-direction: row;
}

.audioblock {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    margin-left: 3%;
}

img {
    width: 50%;
    height: 50%;
    margin-left: 3%;
}

.item {
    display: flex;
    align-items: center;
    flex-direction: column;
}
</style>