<template>
   <div id="app">

    <label for="film_select">Select a Film:</label>
    <select id="film_select" v-model="selectedFilm">
      <option disabled value="">Select a film</option>
      <option v-for="(film, index) in films" :key=index :value="film">{{film.title}}</option>
    </select>

<film-detail v-if="selectedFilm" :film="selectedFilm"></film-detail>

<button @click="addFavourite">Add Film to favourites</button>
<favourite-films :films="favouriteFilms"></favourite-films>
    
</div>

</template>

<script>
import FilmDetail from './components/FilmDetail';
import FavouriteFilm from './components/FavouriteFilm';

export default {
  name: 'App',
  data() {
    return {
      films: [],
      selectedFilm: null,
      favouriteFilms: []
    }
  },
  components: {
    'film-detail': FilmDetail,
    'favourite-films': FavouriteFilm

  },
    mounted(){
      this.fetchFilms();
    },
    methods: {
      fetchFilms: function(){
        fetch("https://ghibliapi.herokuapp.com/films")
        .then((response) => response.json())
        .then((data) => this.films = data)
    
      },
       addFavourite: function(){
       let isPresent = false;
       for (let film of this.favouriteFilms){
         if (this.selectedFilm.title === film.title) {
           isPresent = true;
          }
        }
        if(isPresent){
          return
        } else {
          this.favouriteFilms.push(this.selectedFilm)
        }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
