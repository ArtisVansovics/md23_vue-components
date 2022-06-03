<template>
  <AnimalListContainer />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import AnimalListContainer from "@/components/AnimalListContainer/AnimalListContainer.vue";

export default defineComponent({
  name: "App",
  components: { AnimalListContainer },
});
</script>

<style scoped lang="scss" />
