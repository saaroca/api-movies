<template>
  <div>
    <b-container>
      <b-row>
        <b-col cols="4" v-for="movie in movies" :key="movie.id">
          <b-card
            :title="movie.title"
            :img-src="'https://image.tmdb.org/t/p/w500' + movie.poster_path"
            img-alt="Image"
            img-top
            tag="article"
            style="max-width: 20rem"
            class="mb-2"
          >
            <b-card-text>{{ movie.release_date }}</b-card-text>
            <nuxt-link :to="'/movie/' + movie.id" class="btn btn-primary">Read more</nuxt-link>
          </b-card>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      movies: [],
    }
  },
  asyncData() {
    return axios
      .get(
        'https://api.themoviedb.org/3/movie/popular?api_key=87eef2ec7f5d9505e155d45fb44584cb&language=en-US&page=1'
      )
      .then((response) => {
        return { movies: response.data.results }
      })
  },
}
</script>
