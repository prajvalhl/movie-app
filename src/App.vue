<template>
  <main>
    <Header title="Movie App"></Header>
    <div class="container mt">
      <div class="row">
        <div class="offset-md-3 col-lg-6 p2">
          <div class="card card-body mt-2">
            <movie-form :addMovie="addMovie"></movie-form>
          </div>
          <movie-list :movies="movies" :deleteMovie="deleteMovie"></movie-list>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import Header from "./layout/Header";
import MovieForm from "./components/MovieForm.vue";
import MovieList from "./components/MovieList.vue";

export default {
  name: "App",
  components: { Header, MovieForm, MovieList },
  data() {
    return { movies: [] };
  },
  methods: {
    addMovie(movie) {
      this.movies.push(movie);
      localStorage.setItem("@movies", JSON.stringify(this.movies));
    },
    deleteMovie(id) {
      const index = this.movies.findIndex((movie) => movie.id === id);
      this.movies.splice(index, 1);
      localStorage.setItem("@movies", JSON.stringify(this.movies));
    },
  },
  mounted() {
    const data = JSON.parse(localStorage.getItem("@movies"));
    if (data) {
      try {
        this.movies = data;
      } catch (e) {
        localStorage.removeItem("@movie");
      }
    }
  },
};
</script>

<style>
* {
  padding: 0;
  outline: 0;
  margin: 0;
  box-sizing: border-box;
}
main {
  background-image: url("./assets/lco-movie.jpg");
  background-position: center;
  background-size: cover;
  min-height: 100vh;
}
</style>
