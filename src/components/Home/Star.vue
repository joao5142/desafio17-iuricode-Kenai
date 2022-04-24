<template>
  <div class="star">
    <img :src="require(`@/assets/images/${getUrlImage()}`)" />
  </div>
</template>

<script>
export default {
  name: "Star",
  props: {
    name: String,
  },
  methods: {
    getUrlImage() {
      // let image = require.context("../../assets/images/", false, /\.svg$/);

      if (this.name == "yellow") {
        return "star-yellow.svg";
      } else {
        return "star-white.svg";
      }
    },
  },
};
</script>
<style lang="scss" scoped>
.star {
  display: inline-block;
  width: 20px;
  height: 20px;
  min-width: 20px;

  min-height: 20px;
  margin-right: 2px;
  padding: 0px;
}
.star img {
  width: 20px;
  height: 20px;
  object-fit: cover;
}
</style>