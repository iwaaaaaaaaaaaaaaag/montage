<template>
  <div>
    <draggable v-model="myArray">
      <div v-for="element in myArray" :key="element.id">{{ element.name }}</div>
    </draggable>
  </div>
</template>

<script>
import draggable from "vuedraggable";
export default {
  components: {
    draggable,
  },
  data: () => ({
    myArray: [
      { id: 1, name: "hoge" },
      { id: 2, name: "foo" },
      { id: 3, name: "bar" },
    ],
  }),
};
</script>