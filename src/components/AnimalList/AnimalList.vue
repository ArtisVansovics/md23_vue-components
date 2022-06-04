<template>
  <div class="list">
    <div v-for="({ id, type, name }, index) in animals" class="item" :key="id">
      <div class="box">{{ type }}</div>
      <p>{{ name }}</p>
      <button @click="animalDeleteHandler(index)" class="delete-button">
        X
      </button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "AnimalList",
  props: ["animals"],
  emits: ["deleteAnimal"],
  methods: {
    animalDeleteHandler(index: number) {
      this.$emit("deleteAnimal", index);
    },
  },
});
</script>

<style scoped lang="scss" src="./AnimalList.scss" />
