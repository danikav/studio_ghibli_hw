<template>
   <div id="selected_film">
    <h2>{{film.title}}</h2>
    <p>{{film.description}}</p>
    <p>{{film.release_date}}</p>
  

</div>
</template>

<script>
export default {
  name: 'film-detail',
  props: ['film']

}
</script>

<style>

</style>