<template>
  <div class="list">
    <div v-for="{ id, type, name } in animals" class="item" :key="id">
      <div class="box">{{ type }}</div>
      <p>{{ name }}</p>
      <button class="delete-button">X</button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "AnimalList",
  props: ["animals"],
});
</script>

<style scoped lang="scss" src="./AnimalList.scss" />
