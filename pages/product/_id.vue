.<template>
  <div>
    <v-card :loading="loading" class="mx-auto my-12" max-width="374">
      <template slot="progress">
        <v-progress-linear
          color="deep-purple"
          height="10"
          indeterminate
        />
      </template>

      <v-img
        height="250"
        :src="
          'http://image.tmdb.org/t/p/w600_and_h900_bestv2' +
            this.$route.params.id.poster_path
        "
      />

      <v-card-title>
        <div>Title : {{ this.$route.params.id.title }}</div>
      </v-card-title>

      <v-card-text>
        <v-row align="center" class="mx-0">
          <v-rating
            :value="this.$route.params.id.vote_average/2"
            color="amber"
            dense
            half-increments
            readonly
            size="14"
          />

          <div class="grey--text ml-4">
            <div>Vote : {{ this.$route.params.id.vote_average/2 }}</div>
          </div>
        </v-row>

        <div>
          <div>Overview : {{ this.$route.params.id.overview }}</div>
        </div>
      </v-card-text>

      <v-divider class="mx-4" />
      <div>Popularity : {{ this.$route.params.id.popularity }}</div>
    </v-card>
  </div>
</template>
<script>
export default {}
</script>
<style>
</style>
