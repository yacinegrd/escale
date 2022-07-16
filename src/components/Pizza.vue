<script setup>
import PizzaContainer from "./containers/PizzaContainer.vue";
</script>
<template>
  <div class="align">
    <PizzaContainer v-for="choi in choix" :detail="choi" />
  </div>
</template>
<script>
export default {
  name: "Pizza",
  props: ["lang"],
  data() {
    return {
      choix: {},
    };
  },
  async created() {
    const res = await fetch(`/json/${this.lang}/Pizzas.json`);
    const data = await res.json();
    this.choix = data;
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
