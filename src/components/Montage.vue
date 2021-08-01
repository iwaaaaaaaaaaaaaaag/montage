<template>
  <div>
    <interact
      draggable
      :dragOption="dragOption"
      @dragmove="dragMove"
      :style="style"
    >
      <img :src="imageURL"  
 />
    </interact>
  </div>
</template>

<script>
import interact from "interactjs";

export default {
  props: ["imageURL"],
  data() {
    return {
      axis: {
        x: 0,
        y: 0,
      },
      overlay: 0,
      dragOption: {
        modifiers: [
          //正直よくわからん
          interact.modifiers.restrictRect({
            restriction: "self",
            endOnly: true,
          }),
        ],
      },
    };
  },
  computed: {
    style() {
      return {
        transform: `translate(${this.axis.x}px, ${this.axis.y}px)`,
        position: "relative",
        "z-index": `${this.overlay}`,
      };
    },
  },
  methods: {
    dragMove(event) {
      this.axis.x += event.dx;
      this.axis.y += event.dy;
    },
  },
};
</script>

<style>
.dragMove {
  cursor: url("~@/assets/piko.png"), auto;
}
</style>