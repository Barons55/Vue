<template>
  <div class="about-me" v-if="user">
    <h1>About Me</h1>
    <h3>Name: {{ user.name }}</h3>
    <h3>Surname: {{ user.surname }}</h3>
    <h3>Code: {{ user.code }}</h3>
  </div>
</template>

<script>
export default {
  props: {
    user: Object
  }
};
</script>

<style scoped>
.about-me {
  height: 100%;
}
</style>