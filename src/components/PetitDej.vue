<script setup>
import PetitDejContainer from "./containers/PetitDejContainer.vue";
</script>
<template>
  <div class="align">
    <PetitDejContainer v-for="choi in choix" :detail="choi" :lang="lang" />
  </div>
</template>
<script>
export default {
  name: "PetitDej",
  props: ["lang"],
  data() {
    return {
      choix: {},
    };
  },
  async created() {
    const res = await fetch(`/json/${this.lang}/petit-dej.json`);
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
  gap: 20px;
  margin-bottom: 30px;
}
</style>
