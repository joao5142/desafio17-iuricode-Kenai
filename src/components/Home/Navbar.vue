<template>
  <nav>
    <ul class="d-flex">
      <li>
        <img src="@/assets/images/search.svg" alt="" />
      </li>
      <li>Início</li>
      <li>Minha lista</li>
      <li>
        <img src="@/assets/images/bell.svg" alt="" />
      </li>
      <li>
        <img src="@/assets/images/user.svg" alt="" />
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: "Navbar",
};
</script>

<style lang="scss" scoped>
li {
  font-size: 1.1rem;
  color: $white-color;
  margin-left: 70px;
}
li img {
  width: 24px;
  height: 24px;
}

@media (max-width: 576px) {
  ul {
    margin: 0 auto;
    padding: 0px;
    justify-content: center;
    gap: 30px;
  }
  li {
    margin: 0px;
  }
}
</style>
