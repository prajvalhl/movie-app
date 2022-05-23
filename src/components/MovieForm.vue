<template>
  <form @submit.prevent="onSubmit" class="text-center">
    <input
      class="form-control mb-2"
      type="text"
      placeholder="Jot down a Movie"
      v-model="name"
    />
    <input
      class="form-control mb-2"
      type="text"
      placeholder="Movie URL"
      v-model="url"
    />
    <button class="btn btn-info" type="submit">Add Movie</button>
  </form>
</template>

<script>
import { v4 as uuidv4 } from "uuid";

export default {
  name: "MovieForm",
  props: {
    addMovie: Function,
  },
  data() {
    return {
      name: "",
      url: "",
    };
  },
  methods: {
    onSubmit() {
      this.addMovie({
        name: this.name,
        url: this.url,
        id: uuidv4(),
        data: Date.now(),
      });

      this.name = "";
      this.url = "";
    },
  },
};
</script>

<style></style>
