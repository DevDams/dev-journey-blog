<template>
  <div>
    <div class="banner pt-16 w-full h-72 rounded-md">
      <img :src="require(`../../assets/images/${getImg(article.thumbnail)}`)" alt="article thumbnail" class="w-full h-full object-cover">
    </div>
    <div class="article-info w-11/12 md:w-10/12 lg:w-9/12 max-w-screen-xl mx-auto mt-10">
      <h1 class="text-4xl md:text-5xl font-bold">{{ article.title }}</h1>
      <div class="date mt-4">
        {{ formatDate(article.createdAt) }} - {{ getReadingTime(article.readingStats) }} de lecture
      </div>
    </div>
    <div class="content w-11/12 md:w-10/12 lg:w-9/12 max-w-screen-xl mx-auto mt-10">
      <nuxt-content :document="article" />
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content('articles', params.slug).fetch()
    console.log(article)

    return { article }
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
</style>