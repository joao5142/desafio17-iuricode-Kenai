<template>
  <router-link :to="urlPath">
    <div class="user-container d-flex align-items-center flex-column">
      <div class="user" :class="getClassColor"></div>
      <p class="username">{{ user.username }}</p>
    </div>
  </router-link>
</template>

<script>
export default {
  name: "Perfil",
  props: {
    user: Object,
    color: String,
  },
  computed: {
    getClassColor() {
      if (this.color == "green" || !this.color) {
        return "green-gradient";
      } else if (this.color == "blue") {
        return "blue-gradient";
      } else if (this.color == "purple") {
        return "purple-gradient";
      }
    },
    urlPath() {
      return {
        path: `/home/user/${this.user.id}`,
        params: {
          id: this.user.id,
        },
      };
    },
  },
};
</script>

<style lang="scss" scoped>
.user-container {
  cursor: pointer;
}
.user {
  width: 150px;
  height: 150px;
  border-radius: 50%;
}
.username {
  font-size: 1.3rem;
  text-align: center;
  color: $gray-color;
  margin-top: 20px;
}

.green-gradient {
  background: linear-gradient(180deg, #64fa9b 0%, #5fe36a 100%);
}
.blue-gradient {
  background: linear-gradient(180deg, #4df0f3 0%, #4d7bfd 100%);
}
.purple-gradient {
  background: linear-gradient(225deg, #781fd1 0%, #570eab 100%);
}

@media (max-width: 700px) {
  .user {
    width: 100px;
    height: 100px;
  }
  .username {
    font-size: 1rem;
  }
}
@media (max-width: 466px) {
  .user {
    width: 70px;
    height: 70px;
  }
}
</style>
