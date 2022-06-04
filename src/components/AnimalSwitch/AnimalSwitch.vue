<template>
  <MDBSwitch
    label="Show only cats"
    v-model="displayCats"
    v-on:change="handleDisplayToggle(displayCats)"
  />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { MDBSwitch } from "mdb-vue-ui-kit";

export default defineComponent({
  name: "AnimalSwitch",
  components: {
    MDBSwitch,
  },
  data: () => ({
    displayCats: false,
  }),
  emits: ["toggleDisplayCats"],
  methods: {
    handleDisplayToggle(showCats: boolean) {
      this.$emit("toggleDisplayCats", showCats);
    },
  },
});
</script>

<style scoped lang="scss" src="./AnimalSwitch.scss" />
