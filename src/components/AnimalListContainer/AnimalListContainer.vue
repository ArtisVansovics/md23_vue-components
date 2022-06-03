<template>
  <div class="container">
    <AnimalSwitch />
    <h1>Title</h1>
    <AnimalForm />
    <AnimalList />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import AnimalForm from "@/components/AnimalForm/AnimalForm.vue";
import AnimalSwitch from "@/components/AnimalSwitch/AnimalSwitch.vue";
import AnimalList from "@/components/AnimalList/AnimalList.vue";

export default defineComponent({
  name: "AnimalListContainer",
  components: {
    AnimalSwitch,
    AnimalForm,
    AnimalList,
  },
});
</script>

<style scoped lang="scss" src="./AnimalListContainer.scss" />
