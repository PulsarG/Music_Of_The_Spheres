<template>
  <div class="navbar">
    <button class="btn" @click="setLock('0');" v-bind:class="{ onclick: but[0] }">
      СОЛНЕЧНАЯ СИСТЕМА
    </button>
    <!-- <button class="btn" @click="setLock('1')" v-bind:class="{ onclick: but[1] }">
      ЗВЕЗДЫ
    </button> -->
    <button class="btn" @click="setLock('2')" v-bind:class="{ onclick: but[2] }">
      ИНЫЕ ОБЪЕКтЫ
    </button>
  </div>

  <div class="soni" v-if="!but[0] && !but[2]">
    <p><a href="https://en.wikipedia.org/wiki/Sonification">Сонификация</a> - метод перобразоования измеряемых данных в
      звуковые колебания. </p>
    <p>Все материалы взяты из открытых источников Wiki и NASA</p>
    <iframe width="70%" height="300" src="https://www.youtube.com/embed/3N9RnmwIWbA" title="YouTube video player"
      frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen></iframe>
    <iframe width="70%" height="300" src="https://www.youtube.com/embed/J7STY_H0BEk" title="YouTube video player"
      frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen></iframe>
  </div>
  <audio-libsolar :Items="ItemsSolar" v-show="but[0]"></audio-libsolar>
  <audio-libsolar :Items="ItemsObjects" v-show="but[2]"></audio-libsolar>
  <!--  <audio-libstars :Items="ItemsStars" v-show="but[1]"></audio-libstars>
  <audio-objects :Items="ItemsObjects" v-show="but[2]"></audio-objects> -->
</template>

<script>
import MenuButton from "@/ui/MenuButton.vue";
import AudioLibsolar from "@/components/AudioLibsolar.vue";

import axios from 'axios';

export default {
  components: { MenuButton, AudioLibsolar },
  data() {
    return {
      but: {
        active1: false,
        active2: false,
        active3: false,
      },

      isClick: false,
      ItemsSolar: [{}],
      ItemsStars: [{}],
      ItemsObjects: [{}],
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
    },
    loadArrSolar() {
      try {
        axios.get("https://mots-e43e9-default-rtdb.europe-west1.firebasedatabase.app/solar.json")
          .then((response) => {
            let array = [];
            for (var i in response.data)
              array.push([i, response.data[i]]);
            let j = array.length;
            for (let i = 0; i < j; i++) {
              this.ItemsSolar.push(array[i][1]);
            }
          });
      } catch (e) {
        alert(e);
      }
    },
    loadArrStars() {
      try {
        axios.get("https://mots-e43e9-default-rtdb.europe-west1.firebasedatabase.app/stars.json")
          .then((response) => {
            let array = [];
            for (var i in response.data)
              array.push([i, response.data[i]]);
            let j = array.length;
            for (let i = 0; i < j; i++) {
              this.ItemsStars.push(array[i][1]);
            }
          });
      } catch (e) {
        alert(e);
      }
    },
    loadArrObjects() {
      try {
        axios.get("https://mots-e43e9-default-rtdb.europe-west1.firebasedatabase.app/objects.json")
          .then((response) => {
            let array = [];
            for (var i in response.data)
              array.push([i, response.data[i]]);
            let j = array.length;
            for (let i = 0; i < j; i++) {
              this.ItemsObjects.push(array[i][1]);
            }
          });
      } catch (e) {
        alert(e);
      }
    },
  },
  mounted() {
    this.loadArrSolar();
    this.loadArrStars();
    this.loadArrObjects();
  }
}
</script>

<style scoped>
.navbar {
  width: 50%;
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: auto;
}

.btn {
  width: 20%;
  height: 70%;
  /* background-color: blue; */
  margin: auto;
  border-radius: 50%;
}

.onclick {
  width: 30%;
  height: 90%;
  /* background-color: red; */
  background-color: aqua;
}

.soni {
  width: 50%;
  margin-top: 5%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: auto;
}

iframe {
  margin: 3%;
  width: 70%;
}
</style>