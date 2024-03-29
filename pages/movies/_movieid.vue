<template>
  <Loading v-if="$fetchState.pending" />
  <div v-else class="container single-movie">
    <nuxt-link class="button" :to="{ name: 'index' }">Back</nuxt-link>
    <div class="movie-info">
      <div class="movie-img">
        <img :src="`https://image.tmdb.org/t/p/w500/${movie.poster_path}`" alt="">
      </div>
      <div class="movie-content">
        <h1>Title: {{ movie.title }}</h1>
        <p class="movie-fact tagLine">
          <span>Tagline:</span> {{ movie.tagline }}
        </p>
        <p class="movie-fact tagLine">
          <span>Genres:</span>
          <h v-for="genre in movie.genres" :key="genre">
            {{ `${genre.name}, ` }}
          </h>
        </p>
        <p class="movie-fact">
          <span>Duration:</span> {{ movie.runtime }} minutes
        </p>
        <p class="movie-fact tagLine">
          <span>Languages:</span>
          <h v-for="language in movie.spoken_languages" :key="language">
            {{ `${language.name},` }}
          </h>
        </p>
        <p class="movie-fact">
          <span>Overview:</span> {{ movie.overview }}
        </p>
        <p class="movie-fact">
          <span>Released:</span> 
            {{
              new Date (movie.release_date).toLocaleString('en-us', {
                month: 'long',
                day: 'numeric',
                year: 'numeric',
              })
            }}
        </p>
        <p class="movie-fact tagLine">
          <span>Country:</span>
          <h v-for="country in movie.production_countries" :key="country">
            {{ `${country.name},` }}
          </h>
        </p>
        <p class="movie-fact tagLine">
          <span>Production Companies:</span>
          <h v-for="companies in movie.production_companies" :key="companies">
            {{ `${companies.name},` }}
          </h>
        </p>
        <p class="movie-fact">
          <span>Budget:</span> 
          {{
            movie.budget.toLocaleString('en-us', {
              style: 'currency',
              currency: 'USD',
            })
          }}
        </p>
        <p class="movie-fact">
          <span>Revenue:</span> 
          {{
            movie.revenue.toLocaleString('en-us', {
              style: 'currency',
              currency: 'USD',
            })
          }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
  import axios from "axios"
  import Loading from '~/components/Loading.vue'

  export default {
    components: { Loading },
    name: 'single-movie',
    head () {
      return {
        title: this.movie.title
      }
    },
    data () {
      return {
        movie: '',
      }
    },
    async fetch () {
      await this.getSingleMovie()
    },
    fetchDelay: 1000,
    methods: {
      async getSingleMovie () {
        const data = axios.get(
          `https://api.themoviedb.org/3/movie/${this.$route.params.movieid}?api_key=37ed43a4f8eaa2abd75f9283692947bc&language=en-US`
        )
        const result = await data
        this.movie = result.data
      }
    }
  }
</script>

<style lang="scss" scoped>
  .single-movie {
    color: #fff;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    // justify-content: center;
    padding: 32px 16px;

    .button {
      align-self: flex-start;
      margin-bottom: 32px;
    }

    .movie-info {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 32px;
      color: #fff;

      @media (min-width: 800px) {
        flex-direction: row;
        align-items: flex-start;
      }

      .movie-img {
        img {
          max-height: 500px;
          width: 100%;

          @media (min-width: 800px) {
            max-height: 350px;
            width: initial;
          }
        }
      }

      .movie-content {
        h1 {
          font-size: 35px;
          font-weight: 400;
          margin-bottom: 2rem;
        }

        .movie-fact {
          margin-top: 1rem;
          font-size: 1rem;
          line-height: 1.5;

          span {
            font-weight: 600;
            text-decoration: underline;
          }
        }

        .tagline {
          font-style: italic;

          span {
            font-style: normal;
          }
        }
      }
    }
  }
</style>