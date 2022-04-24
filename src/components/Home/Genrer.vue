<template>
  <div class="genrer">
    {{ title }}
  </div>
</template>

<script>
export default {
  name: "Genrer",
  props: {
    title: String,
  },
};
</script>

<style lang="scss" scoped>
.genrer {
  display: inline-block;
  width: auto;
  padding: 4px 6px;
  font-size: 0.9rem;
  color: $yellow-color;
  background: $gray-dark-color;
  font-weight: 600;
  border-top-right-radius: 7px;
  border-bottom-left-radius: 7px;
}
</style>