<template>
  <div v-bind:class="classNames">
    <Mole
      v-for="(moleState,index) in moleData"
      v-bind:key="index"
      v-bind:active="moleState"
      v-bind:moleId="index"
      @whack="handleClick"
    />
  </div>
</template>

<script>
import Mole from "./Mole";

export default {
  name: "Moles",
  components: {
    Mole
  },
  props: ["moleData", "gameActive"],
  computed: {
    classNames: function() {
      return {
        "moles-container": true,
        "game-active": this.gameActive
      };
    }
  },
  methods: {
    handleClick: function(moleId) {
      this.$emit("whack", moleId);
    }
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

