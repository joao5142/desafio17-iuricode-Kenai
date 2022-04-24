<template>
  <div class="card-movie" @click="showInfo">
    <img :src="require(`@/assets/images/movies/${image}`)" alt="" />

    <div class="card-movie-content">
      <Genrer :title="category" />
      <div class="d-flex">
        <Star v-for="i in 5" :key="i" />
      </div>
      <p class="card-movie-title">{{ name }}</p>
    </div>
  </div>
</template>


<script>
import Genrer from "./Genrer.vue";
import Star from "./Star.vue";
export default {
  props: {
    image: String,
    category: String,
    name: String,
    wallpaper: String,
    description: String,
    duration: String,
    cardClicked: Function,
  },
  components: {
    Genrer,
    Star,
  },
  methods: {
    showInfo() {
      if (this.cardClicked) {
        this.cardClicked({
          image: this.image,
          category: this.category,
          name: this.name,
          wallpaper: this.wallpaper,
          description: this.description,
          duration: this.duration,
        });
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.card-movie {
  width: 300px;
  min-width: 260px;
  height: 380px;
  position: relative;
  cursor: pointer;
}
.card-movie::before {
  content: "";
  position: absolute;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    180deg,
    rgba(24, 24, 24, 0) 0%,
    rgba(24, 24, 24, 0.8) 80.79%
  );
}
.card-movie img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.card-movie-content {
  position: absolute;
  left: 20px;
  bottom: 10px;
  display: flex;
  flex-direction: column;
  gap: 10px;
}
</style>