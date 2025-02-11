<template>
  <div>
    <b-container class="mt-3">
      <b-row>
        <b-col cols="6">
          <img
            :src="'https://image.tmdb.org/t/p/w500' + movie.poster_path"
            alt="portada"
          />
        </b-col>
        <b-col cols="6">
          <b-card :title="movie.title">
            <p class="card-text">{{ movie.overview }}</p>
            <p>Calificación: {{ movie.vote_average }}</p>
          </b-card>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  asyncData({ params }) {
    return axios
      .get(
        `https://api.themoviedb.org/3/movie/${params.id}?api_key=87eef2ec7f5d9505e155d45fb44584cb&language=en-US`
      )
      .then((response) => {
        return { movie: response.data }
      })
  },
}
</script>
