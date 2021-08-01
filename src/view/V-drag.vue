<template>
  <div>
    <div v-for="image in montageImages" :key="image">
      <img
        :class="{ onMouseDown: isMouseDown }"
        style="position: fixed"
        :src="image"
        v-drag
        draggable="false"
        @mousedown="mouseDown"
        @mouseup="mouseUp"
      />
    </div>
  </div>
</template>

<script>
import drag from "@branu-jp/v-drag";

export default {
  directives: {
    drag,
  },
  data() {
    return {
      montageImages: [
        require("@/assets/hana.png"),
        require("@/assets/hidari_me.png"),
        require("@/assets/migi_me.png"),
        require("@/assets/kuchi.png"),
      ],
      isMouseDown: false,
    };
  },
  methods: {
    mouseDown() {
      this.isMouseDown = true;
    },
    mouseUp() {
      this.isMouseDown = false;
    },
  },
};
</script>

<style>
.onMouseDown {
  cursor: url("~@/assets/piko.png"), auto;
}
</style>