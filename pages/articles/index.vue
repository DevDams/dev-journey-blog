<template>
  <div>
    <div class="main">
      <div class="header pt-32 pb-10 w-11/12 md:w-10/12 lg:w-9/12 max-w-screen-xl sm:px-6 mx-auto">
        <h1 class="text-3xl sm:text-5xl font-bold text-center">Tout les articles</h1>
        <div class="categories mt-10 text-center flex flex-col items-center justify-center">
          <h4 class="text-lg font-semibold underline decoration-2">Catégories:</h4>
          <ul class="inline flex flex-wrap items-center justify-center mt-2">
            <li class="cursor-pointer inline-block px-2 py-1 text-sm text-white mx-1 mt-3 rounded-full bg-white bg-gray-500 shadow-md shadow-gray-500/50">Code Snipped</li>
            <li class="cursor-pointer inline-block px-2 py-1 text-sm text-white mx-1 mt-3 rounded-full bg-indigo-500 shadow-md shadow-indigo-500/50">CSS/TailwindCss</li>
            <li class="cursor-pointer inline-block px-2 py-1 text-sm text-white mx-1 mt-3 rounded-full bg-white bg-green-500 shadow-md shadow-green-500/50">Vue.js/Nuxtjs</li>
            <li class="cursor-pointer inline-block px-2 py-1 text-sm text-white mx-1 mt-3 rounded-full bg-white bg-rose-500 shadow-md shadow-rose-500/50">Packages/Plugins</li>
            <li class="cursor-pointer inline-block px-2 py-1 text-sm text-white mx-1 mt-3 rounded-full bg-white bg-emerald-500 shadow-md shadow-emerald-500/50">Frontend</li>
            <li class="cursor-pointer inline-block px-2 py-1 text-sm text-white mx-1 mt-3 rounded-full bg-white bg-sky-500 shadow-md shadow-sky-500/50">Backend</li>
            <li class="cursor-pointer inline-block px-2 py-1 text-sm text-white mx-1 mt-3 rounded-full bg-orange-500 shadow-md shadow-orange-500/50 bg-white">Javascript</li>
          </ul>
        </div>
      </div>
      <hr>
      <div class="article-list mt-16 w-11/12 md:w-11/12 lg:w-10/12 max-w-screen-xl sm:px-6 mx-auto">
        <vue-masonry-wall :items="articles" :options="{width: 400, padding: 12}" @append="append">
          <template v-slot:default="{item}">
            <div class="recent-article-card bg-white mb-10 w-full h-full border-2 border-gray-100 rounded-lg shadow-lg">
              <div class="top h-64 bg-red-100">
                <!-- <img :src="require(`../../assets/images/${getImg(item.thumbnail)}`)" alt="" class="object-cover h-full rounded-lg"> -->
              </div>
              <div class="bottom p-4">
                <nuxt-link :to="`articles/${item.slug}`">
                  <h1 class="text-2xl text-violet-700 font-medium hover:underline">{{ item.title }}</h1>
                </nuxt-link>
                <p class="text-md mt-2 text-gray-900">{{ item.description }}</p>
                <p class="text-sm md:text-md text-gray-400 font-normal mt-2">{{ formatDate(item.createdAt) }} - {{ getReadingTime(item.readingStats) }} de lecture</p>
              </div>
            </div>
          </template>
        </vue-masonry-wall>
        <div class="load-more text-center">
          <button class="mt-6 bg-rose-500 text-white font-bold px-8 py-2 rounded-full shadow-lg shadow-rose-500/50">Afficher plus</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import VueMasonryWall from "vue-masonry-wall";

export default {
  components: {VueMasonryWall},
  data() {
    return {
      articles: [],
      lastArticle: {}
    }
  },
  async mounted() {
    const data = await this.$content('articles').sortBy('createdAt', 'desc').fetch().catch((err) => {
      console.error({ statusCode: 404, message: 'Article introuvable', error: err.message })
    })

    this.articles = data

    console.log(data)
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
</style>