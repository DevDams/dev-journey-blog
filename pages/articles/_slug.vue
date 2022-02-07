<template>
  <div>
    <div class="w-full h-10 bg-green-200 w-full sticky top-16 flex items-center z-50">
      <div class="w-11/12 md:w-10/12 lg:w-9/12 max-w-screen-xl mx-auto">
        <nuxt-link to="/articles">
          <button>
            Retour
          </button>
        </nuxt-link>
      </div>
    </div>
    <div class="banner pt-16 w-full h-72 rounded-md">
      <img :src="require(`../../assets/images/${getImg(article.thumbnail)}`)" alt="article thumbnail" class="w-full h-full object-cover">
    </div>
    <div class="article-info w-11/12 md:w-10/12 lg:w-9/12 max-w-screen-xl mx-auto mt-10">
      <h1 class="text-4xl md:text-5xl font-bold text-indigo-500">{{ article.title }}</h1>
      <div class="date mt-4">
        {{ formatDate(article.createdAt) }} - {{ getReadingTime(article.readingStats) }} de lecture
      </div>
    </div>
    <div class="content w-11/12 md:w-10/12 lg:w-9/12 max-w-screen-xl mx-auto mt-10">
      <nuxt-content :document="article" />
    </div>
    <div class="prev-next-article">
      <PrevNext :prev="prev" :next="next" />
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content('articles', params.slug).fetch()

    const [prev, next] = await $content('articles')
      .only(['title', 'slug'])
      .sortBy('createdAt', 'desc')
      .surround(params.slug)
      .fetch()

    return { 
      article,
      prev,
      next
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

<style>
.nuxt-content {
  color: rgb(17, 24, 39);
}

.nuxt-content h3 {
  font-size: 30px;
  font-weight: 600;
  line-height: 1;
  padding: 8px 0;
}

.nuxt-content img {
  width: 100%;
  height: 400px;
  object-fit: contain;
  margin-top: 15px;
}

p {
  padding: 5px 0;
}

@media (max-width: 640px) {
  .nuxt-content img {
    height: auto;
  }
}
</style>