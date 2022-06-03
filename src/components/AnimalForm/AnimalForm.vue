<template>
  <form class="form" v-on:submit.prevent="handleSubmit">
    <input
      class="input"
      type="text"
      placeholder="Add new animal..."
      v-model="inputValue"
    />
    <select class="select" v-model="speciesSelection">
      <option disabled selected label="Type" />
      <option value="cat">CAT</option>
      <option value="dog">DOG</option>
    </select>
    <button class="button" type="submit">Add</button>
  </form>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "AnimalForm",
  emits: ["addAnimal"],
  data: () => ({
    inputValue: "",
    speciesSelection: "",
    id: 0,
  }),
  methods: {
    handleSubmit() {
      this.$emit("addAnimal", {
        id: (this.id += 1),
        type: this.speciesSelection,
        name: this.inputValue,
      });

      this.inputValue = "";
      this.speciesSelection = "";
    },
  },
});
</script>

<style scoped lang="scss" src="./AnimalForm.scss" />
