<script setup>
import PizzaContainer from "./containers/PizzaContainer.vue";
import SauceContainer from "./containers/SauceContainer.vue";
</script>
<template>
  <h2>{{ lang === "fr" ? "Hamburgers" : "برغر" }}</h2>
  <div class="align">
    <PizzaContainer v-for="choi in choixH" :detail="choi" :lang="lang" />
  </div>
  <h2>{{ lang === "fr" ? "Tacos" : "تاكوس" }}</h2>
  <div class="align">
    <PizzaContainer v-for="choi in choixT" :detail="choi" :lang="lang" />
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
      :lang="lang"
    />
  </div>
  <h2>{{ lang === "fr" ? "Viandes" : "اللحوم" }}</h2>
  <div class="grid">
    <SauceContainer v-for="V in choixV" :detail="V" />
  </div>
  <h2>{{ lang === "fr" ? "Sauces" : "الصلصات" }}</h2>
  <div class="grid">
    <SauceContainer v-for="S in Sauce" :detail="S" />
  </div>
</template>
<script>
export default {
  name: "TH",
  props: ["lang"],

  data() {
    return {
      choixH: {},
      choixT: {},
      choixV: {},
      Sauce: {},
    };
  },
  async created() {
    const resH = await fetch(`/json/${this.lang}/Hamburgers.json`);
    const resT = await fetch(`/json/${this.lang}/Tacos.json`);
    const resSauce = await fetch(`/json/${this.lang}/Sauce.json`);
    const resV = await fetch(`/json/${this.lang}/Viandes.json`);

    const dataH = await resH.json();
    const dataT = await resT.json();
    const dataSauce = await resSauce.json();
    const dataV = await resV.json();

    this.choixH = dataH;
    this.choixT = dataT;
    this.Sauce = dataSauce;
    this.choixV = dataV;
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
