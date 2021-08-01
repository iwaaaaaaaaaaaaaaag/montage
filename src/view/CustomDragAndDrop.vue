<template>
  <div>
    <div
      v-for="image in montageImages"
      :key="image"
      @dragover="dragOver"
      @dragstart="dragstart"
      @dragend="dragEnd"
      :class="{ dragMove: isDragMove }"
    >
      <Montage :imageURL="image" />
    </div>
    <img :src="baseImage" class="base" />
  </div>
</template>

<script>
import Montage from "@/components/Montage";
export default {
  components: {
    Montage,
  },
  data() {
    return {
      montageImages: [
        require("@/assets/hana.png"),
        require("@/assets/hidari_me.png"),
        require("@/assets/migi_me.png"),
        require("@/assets/kuchi.png"),
      ],
      isDragMove: false,
      baseImage: require("@/assets/gokigen_panda_kaonashi.png")
    };
  },
  computed: {
    style() {
      return {
        transform: `translate(${this.x}px, ${this.y}px)`,
      };
    },
  },
  methods: {
    dragOver() {
      console.log("dragOver");
    },
    dragLeave() {
      console.log("dragLeave");
    },
    dragstart() {
      this.overlay = Date.now();
      this.isDragMove = true;
      console.log(this.isDragMove);
    },
    dragEnd() {
      this.isDragMove = false;
      console.log(this.isDragMove);
    },
  },
};
</script>

<style>
.base {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
</style>