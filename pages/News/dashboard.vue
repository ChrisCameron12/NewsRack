<template>
  <div class="container mx-auto">
    Dashboard page
     <div v-for="article in articles" :key="article.id">
      <div>{{ article.content }}</div>
    </div>
    <MainContent :articles="articles"></MainContent>
  </div>
</template>

<script>
import axios from 'axios'
import MainContent from '@/components/MainContent'

export default {
  components: {
    MainContent
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
      articles: []
    }
  }
}

</script>
