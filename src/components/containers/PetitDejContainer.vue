<template>
  <div class="item">
    <img :src="detail.img" alt="" />
    <div class="info">
      <span class="name">{{ detail.name }}</span>
      <span class="price">{{ detail.price }}da</span>
    </div>
    <span class="ingredient">{{ ingredients }}</span>
  </div>
</template>

<script>
export default {
  name: "PetitDejContainer",
  props: {
    detail: Object,
  },
  computed: {
    ingredients() {
      let string = "";
      this.detail.ingredient.map((ing, index, arr) => {
        if (index + 1 === arr.length) string = string + ing + ".";
        else string = string + ing + ", ";
      });
      return string;
    },
  },
};
</script>

<style lang="scss">
.item {
  width: 85%;
  img {
    width: 100%;
    height: 160px;
    object-fit: cover;
    border-radius: 20px;
  }
  .info {
    padding: 10px 10px 5px 0;
    display: flex;
    justify-content: space-between;
    font-weight: 600;
    font-family: "Lora", serif;
    font-size: 20px;
    color: #0a7e8b;
  }
  .ingredient {
    color: #6a6a6a;
  }
}
</style>
