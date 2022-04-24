<template>
  <div class="content">
    <header class="container d-flex justify-content-between pt-4">
      <Logo />
      <Date />
    </header>
    <main class="container">
      <div class="row justify-content-center text-center mt-4">
        <p class="wellcome">Bem-vindo de volta ao Kenai</p>
        <p class="wellcome">Quem está usando?</p>
      </div>

      <div class="row perfil-container">
        <div class="col-12 d-flex justify-content-center perfil-users">
          <Perfil color="purple" :user="{ username: 'Matheus Ramos', id: 1 }" />
          <Perfil color="green" :user="{ username: 'Iuri Silva', id: 2 }" />
          <Perfil color="blue" :user="{ username: 'Vinicius Eiji', id: 3 }" />
        </div>
      </div>
      <div class="row justify-content-center">
        <button class="button-perfil">Adicionar Perfil</button>
      </div>
    </main>
  </div>
</template>

<script>
import Logo from "../components/Logo.vue";
import Date from "../components/Login/Date.vue";
import Perfil from "../components/Login/Perfil.vue";

export default {
  name: "LoginView",
  components: {
    Logo,
    Date,
    Perfil,
  },
};
</script>

<style lang="scss" scoped>
.content {
  width: 100vw;
  height: 100vh;
}
p {
  color: $white-color;
  font-family: "Open Sans";
  font-weight: 300;
}
.wellcome:nth-child(1) {
  font-size: 3rem;
}
.wellcome:nth-child(2) {
  font-size: 1.5rem;
}
.button-perfil {
  width: 200px;
  padding: 10px;
  color: $white-color;
  background-color: $gray-dark-color;
}
.perfil-container {
  margin: 80px 0px;
}
.perfil-users {
  gap: 70px;
}

@media (max-width: 466px) {
  .perfil-users {
    gap: 40px;
  }
}
</style>

