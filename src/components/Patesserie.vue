<script setup>
import BoissonContainer from "./containers/BoissonContainer.vue";
</script>
<template>
  <h2>{{ lang === "fr" ? "Patesserie" : "حلويات" }}</h2>
  <div class="grid">
    <BoissonContainer v-for="choi in choixbc" :detail="choi" :lang="lang" />
  </div>
</template>
<script>
export default {
  name: "Boisson",
  props: ["lang"],
  data() {
    return {
      choixbc: {},
      choixbf: {},
    };
  },
  async created() {
    const resbc = await fetch(`/json/${this.lang}/Patisserie.json`);
    const databc = await resbc.json();
    this.choixbc = databc;
  },
};
</script>
<style lang="scss">
h2 {
  text-align: center;
  color: #0a7e8b;
  font-family: "Lora", serif;
}
.grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
}
</style>
