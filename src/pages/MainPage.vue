<template>
  <div class="navbar">
    <button class="btn" @click="setLock('0')" v-bind:class="{ onclick: but[0] }">
      СОЛНЕЧНАЯ СИСТЕМА
    </button>
    <button class="btn" @click="setLock('1')" v-bind:class="{ onclick: but[1] }">
      ЗВЕЗДЫ
    </button>
    <button class="btn" @click="setLock('2')" v-bind:class="{ onclick: but[2] }">
      ИНЫЕ ОБЪЕКТЫ
    </button>
  </div>

  <audio-libsolar v-show="but[0]"></audio-libsolar>
  <audio-libstars v-show="but[1]"></audio-libstars>
</template>

<script>
import MenuButton from "@/ui/MenuButton.vue";
import AudioLibsolar from "@/components/AudioLibsolar.vue";
import AudioLibstars from "@/components/AudioLibstars.vue"

import AudioItem from '@/ui/AudioItem.vue';
export default {
  components: { MenuButton, AudioLibsolar, AudioLibstars, AudioItem },
  data() {
    return {
      but: {
        active1: false,
        active2: false,
        active3: false,
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
    }
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
}

.onclick {
  width: 30%;
  height: 90%;
  /* background-color: red; */
}
</style>