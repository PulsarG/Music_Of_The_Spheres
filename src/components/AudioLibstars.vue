<template>
    <div class="lib">
        <div class="btns">
            <button class="btn" @click="setLock('1');" v-bind:class="{ onclick: but[1] }">
                Сириус
            </button>
        </div>

        <div class="item" v-show="nItem > 0">

            <div class="head">
                <div class="audioblock">
                    <h3>{{ Items[nItem].name }}</h3>
                    <audio :src='Items[nItem].audio' controls></audio>
                    <p><i>Рекомендуется уменьшить громкость вашего устройства или проигрывателя, т.к. громкость
                            по-умолчанию - максимальная.</i></p>
                </div>
                <img :src='Items[nItem].img' alt="">
            </div>

            <div class="info">
                <div class="text">
                    <h4>
                        {{ Items[nItem].text }}
                    </h4>

                    <a :href='Items[nItem].wiki' target="_blank">{{ Items[nItem].name }} на Вики</a>
                </div>
            </div>

        </div>

    </div>
</template>

<script>
import AudioItem from '@/ui/AudioItem.vue';

import axios from 'axios';

export default {
    components: { AudioItem },
    data() {
        return {
            but: {
                active1: false,
                active2: false,
                active3: false,
                active4: false,
                active5: false,
                active6: false,
                active7: false,
                active8: false,
                active9: false,
                active10: false,
                active11: false,
                active12: false,
                active13: false,
                active14: false,
                active15: false,
                active16: false,
            },

            /* Items: {
                img: "https://upload.wikimedia.org/wikipedia/commons/thumb/0/0d/Africa_and_Europe_from_a_Million_Miles_Away.png/1024px-Africa_and_Europe_from_a_Million_Miles_Away.png",
                audio: "http://drive.google.com/uc?export=view&id=1qoRFm_c0m7oRVFMGsoAIm2UHHY5JkOPP",
                wiki: "https://ru.wikipedia.org/wiki/%D0%97%D0%B5%D0%BC%D0%BB%D1%8F",
            }, */

            Items: [
                {
                    id: 0,
                    img: "",
                    audio: "",
                    wiki: "",
                    text: "",
                    name: ""
                },
            ],

            /*  Items: [], */


            isClick: false,

            nItem: 0,

            aItem: false,
        }
    },
    methods: {

        setLock(n) {
            if (!this.but[n]) {
                this.closeAll();
                this.but[n] = true;
                this.nItem = n;
            } else {
                this.closeAll();
                this.but[n] = false;
                this.nItem = 0;
            }
        },

        closeAll() {
            this.but[0] = false;
            this.but[1] = false;
            this.but[2] = false;
            this.but[3] = false;
            this.but[4] = false;
            this.but[5] = false;
        },

        loadArr() {
            try {
                axios.get("https://mots-e43e9-default-rtdb.europe-west1.firebasedatabase.app/stars.json")
                    .then((response) => {
                        let array = [];
                        for (var i in response.data)
                            array.push([i, response.data[i]]);
                        let j = array.length;
                        for (let i = 0; i < j; i++) {
                            this.Items.push(array[i][1]);
                        }
                    });
            } catch (e) {
                alert(e);
            }
        }
    },
    mounted() {
        this.loadArr();
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