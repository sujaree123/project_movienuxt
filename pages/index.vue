<template>
  <div>
    <v-container>
      <v-row justify="center">
        <v-col cols="5">
          <v-text-field
            v-model="textSearch"
            label="Enter a movie name"
            single-line
            full-width
            hide-details
            type="text"
            color="green accent-2"
          />
        </v-col>
        <v-col cols="1">
          <v-btn
            class="ma-6"
            tile
            color="green accent-2"
            dark
            @click="searchData()"
          >
            Search
          </v-btn>
        </v-col>
      </v-row>
    </v-container>
    <v-row>
      <v-card
        v-for="list in playlist"
        :key="list.id"
        :title="list.title"
        class="mx-auto mb-4"
        max-width="400"
      >
        <v-img
          class="white--text align-end"
          height="300px"
          :src="'http://image.tmdb.org/t/p/w600_and_h900_bestv2' + list.poster_path "
        >
          <v-card-title>{{ list.title }}</v-card-title>
        </v-img>
        <v-card-actions>
          <v-btn
            color="orange"
            text
            target="_blank"
            :href="'https://www.themoviedb.org/movie/' + list.id "
          >
            Details
          </v-btn>
          <nuxt-link :to=" {name: 'product-id', params: { id: list }}">
            <v-btn
              color="orange"
              text
            >
              Score
            </v-btn>
          </nuxt-link>
        </v-card-actions>
      </v-card>
    </v-row>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data () {
    return {
      playlist: null,
      textSearch: '',
      t: this.textSearch
    }
  },
  methods: {
    searchData () {
      axios
        .get(
          'https://api.themoviedb.org/3/search/movie?query=' +
            this.textSearch +
            '&api_key=feb6f0eeaa0a72662967d77079850353'
        )
        .then((Response) => {
          this.playlist = Response.data.results
        })
        .catch((err) => {
          console.log(err)
          this.err = true
        })
    }
  }
}
</script>
<style>
.theme--dark.v-application {
  background-image: url("../assets/imgs/1.jpg");
  background-attachment: fixed;
  background-position: 100% 100%;
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
