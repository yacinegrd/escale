<template>
  <div class="sauce">
    <img :src="detail.img" alt="" />
    <span class="name">{{ detail.name }}</span>
  </div>
</template>

<script>
export default {
  name: "SauceContainer",
  props: ["detail"],
};
</script>

<style lang="scss">
.sauce {
  background-color: white;
  width: 90px;
  box-shadow: 1px 1px 5px rgba(0, 0, 0, 0.25);
  border-radius: 10px;
  border-top: solid 4px #0a7e8b;
  padding: 10px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 20px;
  img {
    width: 70px;
    height: 70px;
  }
  .name {
    font-weight: 500;
    font-size: 14px;
    text-align: center;
  }
}
</style>
