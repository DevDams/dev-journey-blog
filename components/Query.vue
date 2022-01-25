<template>
  <div>
    {{ post }}
    <!-- If search box is not empty -->
    <vue-masonry-wall v-if="post" :items="post" :options="{width: 400, padding: 12}">
      <template v-slot:default="{item}">
        <div v-if="item.title" class="recent-article-card bg-white mb-1 w-full h-full border-2 border-gray-100 rounded-lg shadow-lg">
          <div class="top h-64 bg-sky-100">
            <!-- <img :src="require(`../../assets/images/${getImg(item.thumbnail)}`)" alt="" class="object-cover h-full rounded-lg"> -->
          </div>
          <div class="bottom p-4">
            <!-- <nuxt-link :to="`articles/${item.slug}`">
              <h1 class="text-2xl text-violet-700 font-medium hover:underline">{{ item.title }}</h1>
            </nuxt-link> -->
            <p class="text-md mt-2 text-gray-900">{{ item }}</p>
            <!-- <p class="text-sm md:text-md text-gray-400 font-normal mt-5">{{ formatDate(item.createdAt) }} - {{ getReadingTime(item.readingStats) }} de lecture</p> -->
          </div>
        </div>
      </template>
    </vue-masonry-wall>
    <!-- if not article found -->
    <p v-if="!post">
      Aucun article trouvé
    </p>
  </div>
</template>

<script>
import VueMasonryWall from "vue-masonry-wall"

export default {
  components: {VueMasonryWall},
  props: {
    post: Array
  }
}
</script>

<style scoped>
</style>