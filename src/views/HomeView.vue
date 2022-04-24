<template>
  <div class="content">
    <div class="background-container" :style="inlineStyle">
      <div class="container">
        <header class="pt-4 d-flex justify-content-between">
          <Logo />
          <Navbar class="d-none d-md-flex" />
          <img
            class="hamburguer d-block d-md-none"
            src="@/assets/images/hamburguer.svg"
            alt=""
            @click="isMenuClick = !isMenuClick"
          />
        </header>
        <Navbar v-if="isMenuClick" class="d-flex d-md-none" />

        <main class="mt-5">
          <section class="row">
            <div class="col">
              <Genrer :title="movieCategory" />
            </div>
          </section>

          <section class="row mt-3">
            <div class="col">
              <Star v-for="i in 5" :key="i" name="yellow" />

              <img
                width="17"
                src="@/assets/images/timer.svg"
                class="ms-3 me-3"
              />
              <small class="movie-duration">{{ movieDuration }}</small>
            </div>
          </section>

          <section class="row">
            <div class="col">
              <p class="movie-title">{{ movieName }}</p>

              <p class="movie-description">
                {{ movieDescription }}
              </p>

              <button class="btn-watch-movie">Assistir agora</button>
            </div>
          </section>

          <section class="row mt-5">
            <div class="col">
              <p class="popular-movies-title">Populares</p>

              <div
                class="
                  container-card-movies
                  d-flex
                  justify-content-between
                  pb-4
                "
              >
                <MovieCard
                  v-for="movie in movies"
                  :name="movie.name"
                  :image="movie.image"
                  :category="movie.category"
                  :wallpaper="movie.wallpaper"
                  :description="movie.description"
                  :duration="movie.duration"
                  :key="movie.id"
                  :card-clicked="clickedCard"
                />
              </div>
            </div>
          </section>
        </main>

        <footer class="mt-5">
          <div class="row pt-3 pb-3">
            <div class="col d-flex justify-content-between align-items-center">
              <p class="footer-title">Kenai</p>
              <nav>
                <ul class="d-flex footer-socials">
                  <li>
                    <img src="@/assets/images/instagram.svg" />
                  </li>
                  <li>
                    <img src="@/assets/images/twitter.svg" />
                  </li>
                  <li>
                    <img src="@/assets/images/facebook.svg" />
                  </li>
                </ul>
              </nav>
            </div>
          </div>
        </footer>
      </div>
    </div>
  </div>
</template>

<script>
import Logo from "../components/Logo.vue";
import Genrer from "../components/Home/Genrer.vue";
import Star from "../components/Home/Star.vue";
import MovieCard from "../components/Home/MovieCard.vue";
import Navbar from "../components/Home/Navbar.vue";
import database from "../../database.js";

export default {
  name: "HomeView",
  data() {
    return {
      movieName: "Batman",
      movieBackground: "wallpaper.svg",
      movieCategory: "Ação/Aventura",
      movieDescription: `Após dois anos espreitando as ruas como Batman, Bruce Wayne se encontra nas profundezas mais sombrias de Gotham City. Com poucos aliados confiáveis, o vigilante solitário se estabelece como a personificação da vingança para a população.`,
      movieDuration: "2h 56m",
      isMenuClick: false,
      movies: database,
    };
  },
  components: {
    Logo,
    Genrer,
    Star,
    MovieCard,
    Navbar,
  },
  methods: {
    clickedCard(movie) {
      this.changeInfo(movie);
      console.log(movie);
    },
    changeInfo(movie) {
      this.movieName = movie.name;
      this.movieBackground = movie.wallpaper || "wallpaper.svg";
      this.movieCategory = movie.category;
      this.movieDescription = movie.description;
      this.movieDuration = movie.duration;
    },
  },
  computed: {
    bgImage() {
      return require("@/assets/images/movies/wallpaper/" +
        this.movieBackground);
    },
    inlineStyle() {
      return {
        backgroundImage: `url(${this.bgImage})`,
      };
    },
  },
};
</script>

<style lang="scss" scoped>
.content {
  background-color: $dark-color;
}
.background-container {
  height: 80vh;

  background-size: cover;
  background-attachment: fixed;
  position: relative;
  z-index: 1;
}
.hamburguer {
  color: $white-color;
  width: 32px;
  height: 32px;
  cursor: pointer;
}
.background-container::before {
  content: "";
  position: absolute;
  bottom: 0px;
  width: 100%;
  height: 300px;
  background: linear-gradient(to top, $dark-color 0%, rgba(29, 29, 29, 0) 100%);
  background-size: cover;
  z-index: -2;
}
.container {
  z-index: 1;
}
.movie-duration {
  font-size: 0.9rem;
  color: $white-color;
}
.movie-title {
  font-size: 3rem;
  font-weight: 600;
}
.movie-description {
  max-width: 500px;
  text-align: justify;
}
.btn-watch-movie {
  background: $yellow-color;
  color: $gray-dark-color;
  font-weight: 600;
  padding: 10px 70px;
  border-radius: 4px;
}
.popular-movies-title {
  font-size: 1.3rem;
  position: relative;
}
.popular-movies-title::before {
  content: "";
  position: absolute;
  bottom: -8px;
  height: 2px;
  width: 50px;
  background: $yellow-color;
}
.container-card-movies {
  overflow-x: auto;
  overflow-y: hidden;
  gap: 30px;
  scrollbar-width: 5px;
  position: relative;
  margin: 20px 0px;
}

.container-card-movies::-webkit-scrollbar {
  max-height: 12px;
  position: absolute;
  top: -10px;
}
.container-card-movies::-webkit-scrollbar-track {
  background: #f1f1f1;
}
.container-card-movies::-webkit-scrollbar-thumb {
  background: $gray-dark-color;
  box-shadow: inset 2 2 6px rgba(0, 0, 0, 0.8);
}

.footer-title {
  font-size: 1.8rem;
  font-family: "Mukta";
  font-weight: 700;
}
.footer-socials {
  gap: 40px;
}
</style>
