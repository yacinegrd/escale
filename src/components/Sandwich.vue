<script setup>
import PizzaContainer from "./containers/PizzaContainer.vue";
import SauceContainer from "./containers/SauceContainer.vue";
</script>
<template>
  <div class="align">
    <PizzaContainer v-for="choi in choix" :detail="choi" />
    <PizzaContainer
      :detail="
        lang === 'fr'
          ? {
              name: 'Boisson + Frites',
              price: 200,
              ingredient: [],
              sup: true,
            }
          : {
              name: 'مشروب + بطاطس',
              price: 200,
              ingredient: [],
              sup: true,
            }
      "
    />
  </div>
  <h2>{{ lang === "fr" ? "Sauces" : "الصلصات" }}</h2>
  <div class="grid">
    <SauceContainer v-for="S in Sauce" :detail="S" />
  </div>
</template>
<script>
export default {
  name: "Sandwich",
  props: ["lang"],
  data() {
    return {
      choix: {},
      Sauce: {},
    };
  },
  async created() {
    const res = await fetch(`/json/${this.lang}/sandwichs.json`);
    const resSauce = await fetch(`/json/${this.lang}/Sauce.json`);
    const data = await res.json();
    const dataSauce = await resSauce.json();

    this.choix = data;
    this.Sauce = dataSauce;
  },
};
</script>
<style lang="scss">
.align {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 15px;
}
</style>
