<script setup>
import BoissonContainer from "./containers/BoissonContainer.vue";
</script>
<template>
  <h2>{{ lang === "fr" ? "Boisson Froides" : "المشروبات الباردة" }}</h2>
  <div class="grid">
    <BoissonContainer v-for="choi in choixbc" :detail="choi" />
  </div>
  <h2>{{ lang === "fr" ? "Boisson Chaudes" : "مشروبات ساخنة" }}</h2>
  <div class="grid">
    <BoissonContainer v-for="choi in choixbf" :detail="choi" />
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
    const resbc = await fetch(`/json/${this.lang}/BoissonChaudes.json`);
    const resbf = await fetch(`/json/${this.lang}/BoissonFroides.json`);
    const databc = await resbc.json();
    const databf = await resbf.json();
    this.choixbc = databc;
    this.choixbf = databf;
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
