<template>
    <div class="item">

        <div class="head">
            <div class="audioblock">
                <h3>Земля</h3>
                <audio :src='Items[nItem].audio' controls></audio>
            </div>
            <img :src='Items[nItem].img' alt="">
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

                <a :href='Items[nItem].wiki' target="_blank">ЗЕМЛЯ на Вики</a>
            </div>
        </div>

    </div>
</template>

<script>
export default {
    props: {
        Items: {
            type: Array,
        },
        nItem: Number,
    }

}
</script>

<style scoped>
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