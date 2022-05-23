<template>
  <div class="navbar navbar-dark bg-primary">
    <a class="navbar-brand" href="#">
      <img src="../assets/logo-white.png" class="brand-img" />
    </a>
    <span class="navbar-text text-white">{{ title }}</span>
  </div>
</template>

<script>
export default {
  name: "HeaderComponent",
  props: ["title"],
};
</script>

<style>
.brand-img {
  width: 30px;
}
</style>
