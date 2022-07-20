<template>
  <div class="boisson">
    <img :src="detail.img" alt="" />
    <div class="info">
      <span class="name">{{ detail.name }}</span>
      <span class="price"
        >{{ detail.price }}{{ lang === "fr" ? " da" : "دج " }}</span
      >
    </div>
  </div>
</template>
<script>
export default {
  name: "Boisson",
  props: ["detail", "lang"],
};
</script>
<style lang="scss">
.boisson {
  background-color: white;
  width: 90px;
  height: 200px;
  box-shadow: 1px 1px 5px rgba(0, 0, 0, 0.25);
  border-radius: 10px;
  border-top: solid 4px #0a7e8b;
  padding: 10px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-bottom: 20px;
  img {
    width: 100%;
  }
  .info {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    height: 100%;
    .name {
      font-family: "Lora", serif;
      font-size: 16px;
      color: #0a7e8b;
      font-weight: 600;
      padding: 15px 0 10px 0;
      height: 100%;
      display: flex;
      text-align: center;
      align-items: center;
      justify-content: center;
    }
    .price {
      font-weight: 500;
    }
  }
}
</style>
