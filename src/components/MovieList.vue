<template>
  <ul class="list-unstyled">
    <li class="mt-2" v-for="item in movies" :key="item.id">
      <div class="card text-center">
        <div class="card-body row">
          <div class="col col-8 d-flex justify-content-center flex-column">
            <h4 class="card-title">{{ item.name }}</h4>
            <p class="card-subtitle mb-2 text-muted">
              Added on {{ formattedDate(item.date) }}
            </p>
          </div>
          <div class="col col-4">
            <a
              :href="item.url"
              target="_blank"
              class="btn btn-outline-primary mb-2 btn-block"
              >View Movie</a
            >
            <button
              class="btn btn-outline-danger btn-block"
              @click="deleteMovie(item.id)"
            >
              Delete
            </button>
          </div>
        </div>
      </div>
    </li>
  </ul>
</template>
<script>
import moment from "moment";

export default {
  name: "MovieList",
  props: ["movies", "deleteMovie"],
  methods: {
    formattedDate(date) {
      return moment(date).format("DD/MM/YYYY [at] hh:mm a");
    },
  },
};
</script>
