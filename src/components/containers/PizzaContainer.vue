<template>
  <div :class="detail.sup ? 'sup pizza' : 'pizza'">
    <img
      :src="detail.sup ? '/pics/Sup/coca-frite_150.png' : detail.img"
      alt=""
    />
    <div class="info">
      <div class="np">
        <span class="name">{{ detail.name }}</span>
        <span class="price"
          >{{ detail.price }}{{ lang === "fr" ? " da" : "دج " }}</span
        >
      </div>
      <span class="ingredient">{{ ingredients }}</span>
    </div>
  </div>
</template>
<script>
export default {
  name: "Pizza",
  props: ["detail", "lang"],
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
.pizza {
  background-color: white;
  box-shadow: 1px 1px 5px rgba(0, 0, 0, 0.25);
  display: flex;
  width: 85%;
  border-radius: 100px;
  padding: 5px 20px 5px 8px;
  img {
    width: 83px;
    height: 83px;
    align-self: center;
    margin-right: 13px;
  }
  .info {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    flex-grow: 1;
    font-size: 14px;
    .np {
      padding-top: 5px;
      color: #0a7e8b;
      display: flex;
      align-items: center;
      justify-content: space-between;
      .name {
        font-size: 18px;
        font-weight: 600;
        font-family: "Lora", serif;
      }
      .price {
        font-weight: 600;
        padding-right: 15px;
        font-size: 18px;
      }
    }
    .ingredient {
      width: 100%;
      display: flex;
      margin: 7px 0;
      flex-grow: 1;
      color: #6a6a6a;
    }
  }
}
.sup {
  .info {
    .np {
      padding-top: 0;
      .price {
        align-self: center;
      }
    }
    justify-content: center;
    .ingredient {
      display: none;
    }
    .ar {
      direction: rtl;
      background-color: aqua;
    }
  }
}
</style>
