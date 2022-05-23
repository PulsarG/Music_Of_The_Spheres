
<template>
    <div class="adds">

        <div class="solar">
            <h1>Добавить</h1>
            <div style="display: flex; flex-direction: column; padding: 20px;">
                <input v-model="this.img" type="text" name="title" id="title" placeholder="URL IMG">
                <input v-model="this.audio" type="text" name="title" id="title" placeholder="URL AUDIO">
                <input v-model="this.wiki" type="text" name="title" id="title" placeholder="URL WIKI">
                <input v-model="this.name" type="text" name="date" id="date" placeholder="NAME">
                <textarea v-model="text" name="body" id="body" cols="30" rows="10" placeholder="TEXT"></textarea>

                <div class="btns">
                    <button @click="sendNews('solar');" id="bt" disabled>Добавить к Солнечной Системе</button>

                    <!-- <button @click="sendNews('stars');">Добавить к Звездам</button> -->

                    <button @click="sendNews('objects');" id="btt" disabled>Добавить к Объектам</button>
                </div>
                <input v-model="inp" type="">
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    data() {
        return {
            img: "",
            audio: "",
            wiki: "",
            text: "",
            name: "",
            url: "http://drive.google.com/uc?export=view&id=",

            inp: "",
            pass: ""
        }
    },
    methods: {
        async sendNews(db) {
            await axios.post("https://mots-e43e9-default-rtdb.europe-west1.firebasedatabase.app/" + db + ".json", {
                img: this.img,
                audio: this.url + this.audio,
                wiki: this.wiki,
                text: this.text,
                name: this.name
            });
        }
    },
    watch: {
        inp(v) {
            if (this.pass == v) {
                document.getElementById('bt').removeAttribute('disabled');
                document.getElementById('btt').removeAttribute('disabled');
            }
        }
    }
}
</script>

<style scoped>
.adds {
    width: 100%;
    height: auto;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
}

input {
    height: 50px;
    margin: 10px;
}

.solar {
    width: 50%;
    height: 50%;
}

button {
    width: 35%;
    height: 100px;
    margin: 3%;
}

.btns {
    display: flex;
    flex-direction: row;
    margin: auto;
}
</style>