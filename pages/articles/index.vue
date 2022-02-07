<template>
  <div>
    <div class="main">
      <div class="header pt-28 pb-16 sm:pt-32 sm:pb-10 w-11/12 md:w-10/12 lg:w-9/12 max-w-screen-xl sm:px-6 mx-auto">
        <div class="title-search w-full h-16 flex items-center justify-between">
          <h1 class="text-3xl sm:text-4xl md:text-4xl lg:text-5xl font-bold">{{ title }}</h1>
          <div class="relative h-full flex items-center">
            <input v-model="searchQuery" autocomplete="off" type="text" name="search" id="search" placeholder="Rechercher..." class="bg-gray-100 border-2 border-black h-10 pl-4 text-black text-md outline-none rounded-lg block focus:shadow-lg focus:shadow-black/10 focus:border-2 focus:border-indigo-500">
            <img src="~/assets/svg/magnifier.svg" alt="search-icon" class="w-5 h-5 absolute right-4">
          </div>
        </div>
      </div>
      <hr>
      <div class="article-list mt-16 w-11/12 md:w-11/12 lg:w-10/12 max-w-screen-xl sm:px-6 mx-auto">
        <div class="list mt-10 md:w-full grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
          <!-- Article -->
          <div v-for="article in articles" :key="article.slug" class="recent-article-card bg-white mb-3 w-full h-full border-2 border-gray-100 rounded-lg shadow-lg">
            <div class="top h-64 bg-red-100">
              <!-- <img :src="require(`../assets/images/${getImg(article.thumbnail)}`)" alt="" class="object-cover h-full rounded-lg"> -->
            </div>
            <div class="bottom p-4">
              <nuxt-link :to="`articles/${article.slug}`">
                <h1 class="text-2xl text-violet-700 font-medium hover:underline">{{ article.title }}</h1>
              </nuxt-link>
              <p class="text-md mt-2 text-gray-900">{{ article.description }}</p>
              <p class="text-sm md:text-md text-gray-400 font-normal mt-5">{{ formatDate(article.createdAt) }} - {{ getReadingTime(article.readingStats) }} de lecture</p>
            </div>
          </div>
          <div v-if="articles.length === 0" class="w-full flex items-center justify-center">
            <p class="text-2xl font-medium uppercase">Aucun</p>
          </div>
        </div>
        <div class="load-more text-center mt-16">
          <hr>
          <button class="mt-4 bg-rose-500 text-white font-bold px-8 py-2 rounded-lg shadow-lg shadow-rose-500/50">Afficher plus</button>
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
      searchQuery: '',
      title: 'Tout les articles'
    }
  },
  async mounted() {
    const data = await this.$content('articles').sortBy('createdAt', 'desc').fetch().catch((err) => {
      console.error({ statusCode: 404, message: 'Article introuvable', error: err.message })
    })

    this.articles = data
  },
  watch: {
    async searchQuery(searchQuery) {
      if (!searchQuery) {
        this.articles = await this.$content('articles').sortBy('createdAt', 'desc').fetch().catch((err) => {
          console.error({ statusCode: 404, message: 'Article introuvable', error: err.message })
        })
        this.title = 'Tout les articles'
        return
      }
      this.articles = await this.$content('articles')
        .limit(6)
        .search(searchQuery)
        .fetch()
      this.title = 'Articles trouvés'
    }
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

@media (max-width: 530px) {
  .title-search {
    width: 95%;
    height: 100px;
    margin: auto;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }

  .title-search h1 {
    margin-top: 24px;
  }

  .title-search input {
    height: 40px;
    margin-top: 20px;
  }

  .title-search img {
    margin-top: 20px;
  }
}
</style>