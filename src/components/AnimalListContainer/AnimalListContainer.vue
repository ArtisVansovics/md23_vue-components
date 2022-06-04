<template>
  <div class="container">
    <AnimalSwitch />
    <AnimalForm @addAnimal="addAnimal" />
    <AnimalList :animals="animals" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import AnimalForm from "@/components/AnimalForm/AnimalForm.vue";
import AnimalSwitch from "@/components/AnimalSwitch/AnimalSwitch.vue";
import AnimalList from "@/components/AnimalList/AnimalList.vue";

type Animal = {
  id: number;
  type: string;
  name: string;
};

export default defineComponent({
  name: "AnimalListContainer",
  components: {
    AnimalSwitch,
    AnimalForm,
    AnimalList,
  },
  data: () => ({
    animals: [] as Animal[],
  }),
  created() {
    this.animals = JSON.parse(localStorage.getItem("animals") || "[]");
  },
  watch: {
    animals(newAnimals) {
      localStorage.setItem("animals", JSON.stringify(newAnimals));
    },
  },
  methods: {
    addAnimal(animal: Animal) {
      const newAnimals = [...this.animals];

      newAnimals.push(animal);

      this.animals = newAnimals;
    },
  },
});
</script>

<style scoped lang="scss" src="./AnimalListContainer.scss" />
