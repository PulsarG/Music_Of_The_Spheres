<template>
    <div class="lib">

        <div class="btns">
            <div class="btns" v-for="i in Items" :key="i.name">
                <button class="btn" @click="settLock(i)">
                    {{ i.name }}
                </button>
            </div>
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

export default {
    props: {
        Items: Array,
    },
    components: { AudioItem },
    data() {
        return {

            isClick: false,

            nItem: 0,

            aItem: false,
        }
    },
    methods: {

        settLock(i) {
            this.nItem = this.Items.indexOf(i);
        },
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
    flex-direction: row;
}

.btn {
    width: 60%;
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