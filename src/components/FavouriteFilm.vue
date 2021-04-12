<template>
<div id="favourite_films">
    <h2>Favourite Films</h2>
    <ul v-for="(film, index) in films" :key="index" :film="film">
      <li>{{film.title}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'favourite-films',
  props: ['films']
}
</script>

<style>

</style>