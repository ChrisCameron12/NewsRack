<template>
<div>
<navigation />
  <div class="container">
    <div>
      <h1 class="title">
        newspaper-rack
      </h1>
      <h2 class="subtitle">
        A News rack with my fav news websites
      </h2>
      <div class="links">
        <nuxt-link
          :to="'/news/dashboard/'"
          class="button--green"
        >
          Go to News Rack
        </nuxt-link>
      </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Navigation from '@/components/Navigation'

export default {
  components: {
    Navigation
  },

  asyncData ({ params, error }) {
    return axios.get(`https://newsapi.org/v2/top-headlines?country=nz&apiKey=8b469ee074b84b7881eac024779889e6`)
      .then((res) => {
        return {
          articles: res.data

        }
      })
      .catch((e) => {
        console.log(e)
      })
  },
  data () {
    return {

    }
  }
}

</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
