<template>
  <div>
    <div class="main h-full">
      <!-- Banner -->
      <div class="hero w-full h-[550px] pt-16 border-b shadow-sm">
        <div class="w-10/12 max-w-screen-xl h-full mx-auto flex items-center justify-between">
          <div class="left text-center w-full">
            <div class="sm:px-6">
              <h2 class="text-5xl sm:text-7xl font-bold">Bienvenue sur <span class="logo">Dev-x</span></h2>
              <p class="text-xl sm:text-3xl text-gray-700 mt-5">Découvre, apprends, progresse !</p>
              <nuxt-link to="/articles">
                <button class="mt-6 bg-indigo-500 text-white font-bold px-8 py-2 rounded-lg shadow-lg shadow-indigo-500/50">Explorer</button>
              </nuxt-link>
            </div>
          </div>
        </div>
      </div>
      <!-- Last article -->
      <div class="main-content w-11/12 md:w-10/12 lg:w-9/12 max-w-screen-xl px-4 sm:px-6 mx-auto">
        <div class="last-article-card mt-16">
          <h4 class="underline decoration-indigo-500 text-center decoration-wavy font-extrabold text-2xl">Dernier article publié</h4>
          <div v-if="lastArticle" class="last-card relative flex flex-col-reverse md:flex md:flex-row md:items-center mt-16 w-full mx-auto md:w-full h-auto border-2 border-gray-100 shadow-lg rounded-md bg-white z-10">
            <div class="left p-5 w-full md:w-1/2 h-full rounded-lg">
              <nuxt-link :to="`articles/${lastArticle.slug}`">
                <h1 class="text-2xl sm:text-3xl md:text-3xl text-indigo-700 font-medium hover:underline"> {{ lastArticle.title }} </h1>
              </nuxt-link>
              <p class="text-md mt-4 font-medium text-gray-800">{{ lastArticle.description }}</p>
              <p class="text-sm sm:text-md text-gray-400 font-normal mt-4">{{ formatDate(lastArticle.createdAt) }} - {{ getReadingTime(lastArticle.readingStats) }} de lecture</p>
            </div>
            <div v-if="getImg(lastArticle.thumbnail)" class="right w-full md:w-1/2 h-auto rounded-lg">
              <img :src="require(`../assets/images/${getImg(lastArticle.thumbnail)}`)" alt="" class="md:absolute top-0 right-0 object-cover h-full w-full md:w-1/2 rounded-lg">
            </div>
          </div>
        </div>
      </div>
      <!-- Articles recents -->
      <div class="recent-main-content w-11/12 md:w-10/12 lg:w-9/12 max-w-screen-xl mx-auto mt-28">
        <h4 class="underline text-center decoration-indigo-500 decoration-wavy font-extrabold text-2xl">Articles récents</h4>
        <div v-if="recentArticles" class="recent-articles mt-16 w-11/12 mx-auto md:w-full grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6 h-auto">
          <div v-for="article in recentArticles" :key="article.slug" class="recent-article-card bg-white mb-2 w-full h-full border-2 border-gray-100 rounded-lg shadow-lg">
            <div v-if="getImg(article.thumbnail)" class="top h-64 bg-red-100">
              <img :src="require(`../assets/images/${getImg(article.thumbnail)}`)" alt="" class="object-cover h-full rounded-lg">
            </div>
            <div class="bottom p-4">
              <nuxt-link :to="`articles/${article.slug}`">
                <h1 class="text-2xl text-indigo-700 font-medium hover:underline">{{ article.title }}</h1>
              </nuxt-link>
              <p class="text-md mt-2 text-gray-900">{{ article.description }}</p>
              <p class="text-sm md:text-md text-gray-400 font-normal mt-2">{{ formatDate(article.createdAt) }} - {{ getReadingTime(article.readingStats) }} de lecture</p>
            </div>
          </div>
        </div>
        <div class="load-more text-center mt-16">
          <hr>
          <nuxt-link to="/articles">
            <button class="mt-4 bg-rose-500 text-white font-bold px-8 py-2 rounded-lg shadow-lg shadow-rose-500/50">Tout les articles</button>
          </nuxt-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      articles: [],
      lastArticle: [],
      recentArticles: []
    }
  },
  async mounted() {
    this.articles = await this.$content('articles').sortBy('createdAt', 'desc').fetch().catch((err) => {
      console.error({ statusCode: 404, message: 'Article introuvable', error: err.message })
    })
    
    this.lastArticle = this.articles.shift()
    this.recentArticles = this.articles
  },
  methods: {
    getImg(img) {
      if (img) {
        const image = img

        const imgName = image.split('/')
        console.log(imgName[imgName.length - 1])
        return imgName[imgName.length - 1]
      } else {
        console.log('bobo')
      }
    },
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('fr', options)
    },
    getReadingTime(obj) {
      if (obj) {
        const data = JSON.stringify(obj)
        const pop = data.split(':')

        const reading = pop[1].split(',')[0]
        const time = reading.split(' ')


        return `${time[0][1]} ${time[1]}`
      } else {
        console.error('No element found')
      }
    }
  },
}
</script>

<style scoped>
body {
  font-family: 'Readex Pro', sans-serif;
}

.hero {
  background: url('@/assets/images/hero.jpg');
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
}

@media (max-width: 490px) {
  .main-content, .recent-main-content {
    width: 100%;
    margin-left: auto;
    margin-right: auto;
  }
}
</style>
