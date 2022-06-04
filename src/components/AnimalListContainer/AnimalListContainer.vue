<template>
  <div class="content-container">
    <div class="row-top">
      <AnimalSwitch @toggleDisplayCats="toggleDisplayCats" />
    </div>
    <AnimalForm @addAnimal="addAnimal" />
    <AnimalList :animals="animalsDisplayed" @deleteAnimal="deleteAnimal" />
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

type DisplayAnimals = "all" | "cats";

export default defineComponent({
  name: "AnimalListContainer",
  components: {
    AnimalSwitch,
    AnimalForm,
    AnimalList,
  },
  data: () => ({
    animals: [] as Animal[],
    displayAnimals: "all" as DisplayAnimals,
  }),
  created() {
    this.animals = JSON.parse(localStorage.getItem("animals") || "[]");
  },
  computed: {
    animalsOnlyCats() {
      return this.animals.filter((animal) => animal.type === "cat");
    },
    animalsDisplayed() {
      if (this.displayAnimals === "cats") {
        return this.animalsOnlyCats;
      }

      return this.animals;
    },
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
    deleteAnimal(index: number) {
      const newAnimals = [...this.animals];

      newAnimals.splice(index, 1);

      this.animals = newAnimals;
    },
    toggleDisplayCats(displayCats: boolean) {
      if (!displayCats) {
        this.displayAnimals = "cats";
      } else {
        this.displayAnimals = "all";
      }
    },
  },
});
</script>

<style scoped lang="scss" src="./AnimalListContainer.scss" />
