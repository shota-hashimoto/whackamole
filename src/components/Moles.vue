<template>
  <div v-bind:class="classNames">
    <Mole
      v-for="(moleState, index) in moleData"
      v-bind:key="index"
      v-bind:active="moleState"
      v-bind:moleId="index"
      v-on:whack="handleWhack"
    />
  </div>
</template>

 <script>
import Mole from "./Mole";
export default {
  name: "Moles",
  props: ["moleData", "gameActive"],
  methods: {
    handleWhack: function(moleId) {
      this.$emit("whack", moleId);
    }
  },
  computed: {
    classNames: function() {
      return {
        "moles-container": true, // 必ず表示する
        "game-active": this.gameActive // ゲームが遊ばれている時だけ
      };
    }
  },
  components: {
    Mole
  }
};
</script>

 <style>
.moles-container {
  margin-top: 20px;
  display: flex;
  justify-content: space-between;
  opacity: 0.5;
  transition: opacity 0.3s ease;
}
.moles-container.game-active {
  opacity: 1;
}
</style>