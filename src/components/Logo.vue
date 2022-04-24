<template>
  <p class="logo">Kenai</p>
</template>

<script>
export default {
  name: "Logo",
};
</script>

<style lang="scss" scoped>
.logo {
  display: inline-block;
  font-family: "Mukta";
  font-weight: 700;
  font-size: 1.8rem;
  background: $gradient-default-color;
  background-size: contain;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
</style>